
# Example Log


"""
(main) C:\Projects\vinai\Day01-lab-assignment-main>python solution/solution.py
=== Comparing models ===
gpt4o_response: Temperature controls the randomness of the output by adjusting the probability distribution of the next word, while top_p (nucleus sampling) limits the selection to a subset of the most probable words whose cumulative probability meets a specified threshold.
mini_response: Temperature controls the randomness of the generated output by scaling the probabilities of potential next words, while top_p (nucleus sampling) restricts the selection to a subset of words whose cumulative probability exceeds a specified threshold, allowing for more focused sampling.
gpt4o_latency: 2.46974360011518
mini_latency: 1.5988014000467956
gpt4o_cost_estimate: 0.0005066666666666667

=== Starting chatbot (type 'quit' to exit) ===
You: Xin chao ban ten la gi
Assistant: Xin chào! Tôi là một trợ lý ảo được phát triển bởi OpenAI và không có tên riêng. Tôi ở đây để giúp trả lời các câu hỏi và cung cấp thông tin mà bạn cần. Bạn cần giúp gì không?
You: Ten toi la MK, nho nha
Assistant: Xin chào MK! Rất vui được gặp bạn. MK cần tôi hỗ trợ gì không?
You: Ten toi la gi
Assistant: Bạn đã nói rằng tên bạn là MK. Bạn cần hỗ trợ thêm điều gì không?
You: ten toi la gi
Assistant: Bạn đã cho biết tên bạn là MK. Nếu có thông tin nào khác bạn muốn chia sẻ hoặc có câu hỏi nào, hãy cho tôi biết nhé!
You: ten toi la gi
Assistant: Xin lỗi, nhưng tôi không thể biết tên của bạn trừ khi bạn cung cấp thông tin đó. Nếu bạn đã cho biết tên mình trước đó là MK, tôi chỉ có thể dựa trên thông tin đó. Nếu có thắc mắc nào khác, đừng ngần ngại cho tôi biết nhé!
You: quit
Goodbye!
"""

(main) C:\Projects\vinai\Day01-lab-assignment-main>python solution/solution.py
=== Comparing models ===
gpt4o_response: Temperature controls the randomness of model output by scaling logits before sampling, with higher values leading to more diverse outputs, while top_p (nucleus sampling) restricts the sampling pool to the smallest set of tokens whose cumulative probability exceeds a threshold p, ensuring coherent but varied responses.
mini_response: Temperature controls the randomness of the output by scaling the probabilities of predicted tokens, while top_p (nucleus sampling) limits the selection to the smallest set of tokens whose cumulative probability exceeds a specified threshold, ensuring a balance between diversity and coherence in the generated text.
gpt4o_latency: 1.8224164999555796
mini_latency: 2.1489494000561535
gpt4o_cost_estimate: 0.0006133333333333334

=== Starting chatbot (type 'quit' to exit) ===
You: Hãy kể cho tôi một sự thật thú vị về Việt Nam

--- temperature = 0.0 ---
Một sự thật thú vị về Việt Nam là đất nước này có một hệ thống hang động lớn nhất thế giới, đó là hang Sơn Đoòng. Hang Sơn Đoòng nằm trong Vườn quốc gia Phong Nha-Kẻ Bàng, tỉnh Quảng Bình. Hang động này được phát hiện vào năm 1991 bởi một người dân địa phương tên là Hồ Khanh, nhưng mãi đến năm 2009 mới được công bố rộng rãi sau khi một đoàn thám hiểm người Anh tiến hành khảo sát. Hang Sơn Đoòng có kích thước khổng

--- temperature = 0.5 ---
Một sự thật thú vị về Việt Nam là quốc gia này là nơi duy nhất trên thế giới có một loại động vật rất đặc biệt được gọi là sao la. Sao la, còn được biết đến với tên gọi "kỳ lân châu Á," là một trong những loài động vật có vú hiếm nhất và ít được biết đến nhất. Nó được phát hiện lần đầu tiên vào năm 1992 trong các khu rừng rậm của dãy Trường Sơn, gần biên giới giữa Việt Nam và Lào. Sao la có ngoại hình giống như một con linh

--- temperature = 1.0 ---
Một sự thật thú vị về Việt Nam là đất nước này là một trong những nước sản xuất cà phê lớn nhất thế giới. Việt Nam đứng thứ hai, chỉ sau Brazil, về sản lượng cà phê xuất khẩu. Loại cà phê nổi tiếng nhất của Việt Nam là cà phê Robusta, chiếm phần lớn sản lượng cà phê của đất nước. Ngoài ra, văn hóa thưởng thức cà phê ở Việt Nam cũng rất độc đáo với nhiều biến thể như cà phê sữa đá, cà phê trứng và cà phê dừa,

--- temperature = 1.5 ---
Một sự thật thú vị về Việt Nam là đây là quốc gia đứng thứ hai trên thế giới về xuất khẩu cà phê, chỉ sau Brazil. Cà phê là một phần quan trọng của nền kinh tế Việt Nam và cũng là một phần không thể thiếu trong văn hóa ẩm thực địa phương. Việt Nam nổi tiếng với loại cà phê robusta, chiếm phần lớn sản lượng xuất khẩu. Ngoài ra, phong cách uống cà phê của người Việt cũng rất độc đáo, như cà phê sữa đá, cà phê trứng hay cà phê d

## attemp 2

========== Exercise 2.1: Temperature sensitivity ==========

--- temperature = 0.0 ---
Một sự thật thú vị về Việt Nam là đất nước này có một hệ thống hang động lớn nhất thế giới, đó là hang Sơn Đoòng. Hang Sơn Đoòng nằm trong Vườn quốc gia Phong Nha-Kẻ Bàng, tỉnh Quảng Bình. Hang động này được phát hiện vào năm 1991 bởi một người dân địa phương tên là Hồ Khanh, nhưng mãi đến năm 2009 mới được công bố rộng rãi sau khi một đoàn thám hiểm người Anh tiến hành khảo sát. Hang Sơn Đoòng có kích thước khổng lồ, với chiều dài hơn 5 km, cao 200 m và rộng 150 m, đủ lớn để chứa cả một tòa nhà chọc trời 40 tầng. Bên trong hang có cả một hệ sinh thái riêng biệt với rừng cây, sông ngầm và các loài động thực vật độc đáo.

--- temperature = 0.5 ---
Một sự thật thú vị về Việt Nam là đất nước này sở hữu một trong những hệ thống hang động lớn nhất thế giới, đó là Hang Sơn Đoòng. Được phát hiện vào năm 1991 và chính thức khảo sát vào năm 2009, Hang Sơn Đoòng nằm trong Vườn quốc gia Phong Nha-Kẻ Bàng, tỉnh Quảng Bình. Hang động này có kích thước khổng lồ với chiều cao đủ để chứa một tòa nhà 40 tầng và chiều rộng có thể đủ cho một chiếc máy bay Boeing 747 bay qua. Bên trong hang có cả một hệ sinh thái riêng với rừng cây, sông ngầm và các loại động thực vật đặc biệt, tạo nên một cảnh quan vô cùng kỳ vĩ và độc đáo.

--- temperature = 1.0 ---
Một sự thật thú vị về Việt Nam là quốc gia này có hệ thống hang động tự nhiên vô cùng phong phú và đẹp mắt, trong đó có hang Sơn Đoòng ở tỉnh Quảng Bình. Hang Sơn Đoòng được công nhận là hang động lớn nhất thế giới, với chiều cao đủ để chứa một tòa nhà 40 tầng và chiều rộng có thể đủ cho một máy bay Boeing 747 bay qua. Hang động này còn chứa cả một khu rừng và một hệ sinh thái riêng, tạo nên một cảnh quan vô cùng kỳ vĩ và độc đáo.

--- temperature = 1.5 ---
Một sự thật thú vị về Việt Nam là đất nước này có một hệ thống hang động lớn và kỳ vĩ, trong đó nổi tiếng nhất là hang Sơn Đoòng. Hang Sơn Đoòng nằm ở Quảng Bình và được xem là hang động lớn nhất thế giới. Hang này được khám phá vào năm 2009 và có thể chứa cả một tòa nhà chọc trời bên trong. Đặc biệt, hang Sơn Đoòng có hệ sinh thái độc đáo với rừng nhiệt đới và dòng sông ngầm bên trong. Sự kỳ vĩ và độc đáo của hang động này đã thu hút rất nhiều nhà thám hiểm và du khách từ khắp nơi trên thế giới.

Đây là log của tôi: 
"""
(main) C:\Projects\vinai\Day01-lab-assignment-main>python solution/solution.py
=== Comparing models ===
gpt4o_response: Temperature controls the randomness of the output by adjusting the probability distribution of the next word, while top_p (nucleus sampling) limits the selection to a subset of the most probable words whose cumulative probability meets a specified threshold.
mini_response: Temperature controls the randomness of the generated output by scaling the probabilities of potential next words, while top_p (nucleus sampling) restricts the selection to a subset of words whose cumulative probability exceeds a specified threshold, allowing for more focused sampling.
gpt4o_latency: 2.46974360011518
mini_latency: 1.5988014000467956
gpt4o_cost_estimate: 0.0005066666666666667

=== Starting chatbot (type 'quit' to exit) ===
You: Xin chao ban ten la gi
Assistant: Xin chào! Tôi là một trợ lý ảo được phát triển bởi OpenAI và không có tên riêng. Tôi ở đây để giúp trả lời các câu hỏi và cung cấp thông tin mà bạn cần. Bạn cần giúp gì không?
You: Ten toi la MK, nho nha
Assistant: Xin chào MK! Rất vui được gặp bạn. MK cần tôi hỗ trợ gì không?
You: Ten toi la gi
Assistant: Bạn đã nói rằng tên bạn là MK. Bạn cần hỗ trợ thêm điều gì không?
You: ten toi la gi
Assistant: Bạn đã cho biết tên bạn là MK. Nếu có thông tin nào khác bạn muốn chia sẻ hoặc có câu hỏi nào, hãy cho tôi biết nhé!
You: ten toi la gi
Assistant: Xin lỗi, nhưng tôi không thể biết tên của bạn trừ khi bạn cung cấp thông tin đó. Nếu bạn đã cho biết tên mình trước đó là MK, tôi chỉ có thể dựa trên thông tin đó. Nếu có thắc mắc nào khác, đừng ngần ngại cho tôi biết nhé!
You: quit
Goodbye!
"""