# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Đã triển khai đầy đủ các TODO trong `solution.py`:

- `call_openai` — gọi GPT-4o, đo độ trễ, trả về `(text, latency)`.
- `call_openai_mini` — tái sử dụng `call_openai` với `model=OPENAI_MINI_MODEL`.
- `compare_models` — gọi cả hai model, ước tính chi phí output cho GPT-4o.
- `streaming_chatbot` — vòng lặp dòng lệnh, stream từng chunk, giữ 3 lượt gần nhất.
- Bonus: `retry_with_backoff`, `batch_compare`, `format_comparison_table`.

Toàn bộ kiểm thử pass với `pytest tests/ -v`.
Xem log mẫu `example_log.md` để tham khảo cách thức hoạt động và output.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature

Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Tôi chạy 2 lần với cùng prompt: ở `temperature=0.0`, cả hai lần đều cho ra cùng một chủ đề (hang Sơn Đoòng) với nội dung gần như trùng khớp, model luôn chọn token xác suất cao nhất nên kết quả ổn định, dễ tái lập. 
Khi tăng lên 0.5–1.0, chủ đề bắt đầu phân tán (lần 1: sao la, cà phê; lần 2: vẫn Sơn Đoòng nhưng cách diễn đạt và độ dài khác hẳn), nghĩa là model dám lấy mẫu từ các token có xác suất thấp hơn. Ở 1.5, độ ngẫu nhiên cao nhất: phong cách viết thay đổi rõ và độ dài dao động mạnh, tuy lần thử của tôi chưa thấy hallucination rõ rệt, nhưng phân phối token bị làm phẳng khiến nguy cơ bịa đặt tăng lên khi prompt khó hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ chọn `temperature` thấp, khoảng 0.2, 0.3. Chatbot hỗ trợ khách hàng cần câu trả lời nhất quán, có thể tái lập, bám sát chính sách và tài liệu sản phẩm, giá trị thấp giảm thiểu sáng tạo không cần thiết và hạn chế bịa đặt thông tin sai về sản phẩm. Tôi vẫn để khác 0 một chút để tránh câu trả lời cứng nhắc, máy móc và giữ giọng điệu tự nhiên, đồng thời cho phép model chọn cách diễn đạt phù hợp nếu cùng câu hỏi được hỏi lại với ngữ cảnh khác.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí

Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Tổng số token output mỗi ngày: 10.000 × 3 × 350 = 10.500.000 token = 10.500K  token.
> - GPT-4o: 10.500 × $0.010 = $105/ngày (apx. $3.150/tháng)
> - GPT-4o-mini: 10.500 × $0.0006 = $6.30/ngày (apx. $189/tháng)
> Tỷ lệ chi phí: $0.010 / $0.0006 ≈ 16.7 lần. GPT-4o đắt hơn GPT-4o-mini khoảng 16–17× trên workload này (xét riêng output token, nếu tính cả input thì tỷ lệ tương tự vì giá input cũng chênh khoảng 16–17×). Trên quy mô năm, khoản chênh là ~$36K/năm.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> **GPT-4o xứng đáng:** Các tác vụ suy luận phức tạp và rủi ro cao, ví dụ trợ lý phân tích báo cáo tài chính/y tế, sinh code cho hệ thống production, hay agent điều phối nhiều bước (planning + tool use). Sai sót ở đây tốn nhiều tiền và uy tín hơn nhiều so với chênh lệch API, GPT-4o cho chất lượng suy luận, độ chính xác và khả năng tuân thủ instruction tốt hơn rõ rệt.

> **GPT-4o-mini tốt hơn:** Các tác vụ khối lượng lớn, đơn giản, độ trễ nhạy cảm, ví dụ phân loại intent, tóm tắt ngắn, gắn tag/email routing, autocomplete, hoặc tier 1 của một pipeline có fallback sang GPT-4o khi confidence thấp. Ở đây, mini nhanh hơn, rẻ hơn 16×, và chất lượng đã đủ ngưỡng dùng được; tiết kiệm chi phí cho phép phục vụ nhiều người dùng hơn với cùng ngân sách.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming

**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất trong các giao diện hội thoại trực tiếp với người dùng cuối, chatbot, copilot lập trình, trợ lý viết văn bản. Dặc biệt khi phản hồi dài (vài giây tới vài chục giây). Người dùng nhìn thấy token đầu tiên sau ~300ms thay vì chờ phản hồi đầy đủ, nên *perceived latency* giảm mạnh và họ có thể đọc, ngắt sớm hoặc đổi hướng câu hỏi, trải nghiệm gần với "đang nói chuyện" chứ không phải "đang submit form". Ngược lại, non-streaming phù hợp hơn cho các lời gọi backend hoặc batch: khi response cần được parse JSON/validate/structured-output trước khi dùng, khi cần đo độ dài/chi phí trước khi commit, khi gọi từ workflow phi-tương tác (cron job, ETL, đánh giá offline), hoặc khi tích hợp với hệ thống chỉ chấp nhận một response duy nhất (ví dụ tool call trả về function arguments hoàn chỉnh). Trong các tình huống đó, streaming chỉ làm phức tạp code mà không cải thiện UX vì không có người dùng đang đợi nhìn ký tự xuất hiện.


## Danh Sách Kiểm Tra Nộp Bài
- [x] Tất cả tests pass: `pytest tests/ -v`
- [x] `call_openai` đã triển khai và kiểm thử
- [x] `call_openai_mini` đã triển khai và kiểm thử
- [x] `compare_models` đã triển khai và kiểm thử
- [x] `streaming_chatbot` đã triển khai và kiểm thử
- [x] `retry_with_backoff` đã triển khai và kiểm thử
- [x] `batch_compare` đã triển khai và kiểm thử
- [x] `format_comparison_table` đã triển khai và kiểm thử
- [x] `exercises.md` đã điền đầy đủ
- [x] Sao chép bài làm vào folder `solution` và đặt tên theo quy định
