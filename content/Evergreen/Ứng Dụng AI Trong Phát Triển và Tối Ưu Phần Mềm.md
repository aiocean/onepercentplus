# Sử dụng AI để giải quyết các vấn đề trong phát triển phần mềm

## Introduction

Để sử dụng Gen AI được hiệu quả, trước hết cần phải có một cái nhìn tổng quan về GenAI, ưu và nhược điểm của nó. Song ở đây ta chỉ nói sơ lược.

### Gen AI là gì?

Generative AI (Gen AI) là một nhánh trong lĩnh vực trí tuệ nhân tạo, dựa trên thuật toán máy học để khám phá và mô hình hóa các pattern trong dữ liệu được train. Và từ đó có thể tạo ra những nội dung mới dựa vào input mà người dùng cung cấp.

Để dễ hiểu hơn, ta sẽ lấy ví dụ với trường hợp generate text:

Bạn cung cấp một khối lượng lớn văn bản cho một thuật toán học máy, Qua quá trình phân tích và học hỏi, thuật toán này sẽ nhận diện các mô hình (pattern) và xây dựng một mô hình ngôn ngữ (languate model). Sau đó, bạn có thể sử dụng model đã học để tạo ra văn bản mới (inference): bạn đưa vào một đoạn văn bản còn thiếu và để trống một số phần, và model sẽ tìm kiếm và đối chiếu mô hình trong đoạn văn đó với những pattern đã học được từ dữ liệu ban đầu để đề xuất những từ ngữ phù hợp nhất.

Trước khi generative AI và các Large Language Models (LLMs) trở nên phổ biến, Chúng ta cũng có nhiều mô hình máy học phục vụ riêng cho từng mục đích, ví dụ như :

- Text Classification: phân loại text vào trong từng class cụ thể.
- Text Summarization: Rút gọn đoạn text dài.
- Sentiment Analysis: Xác định cảm xúc trong đoạn text

Những model này được train để làm một việc cụ thể dựa trên các bộ data được đánh dấu (human-labeled datasets), và không thể mở rộng khả năng qua các công việc khác.

Gen AI có một cách tiếp cận khác - mục tiêu của nó không phải là một nhiệm vụ được xác định trước mà là để hiểu và phản ánh các pattern trong dữ liệu. Nó được train trên các tập dữ liệu khổng lồ (không có label).

Hay nói cách khác, khả năng của nó chỉ có một: điền vào chỗ trống, bằng cách khớp input với các pattern mà nó học được. Nhưng chính sự đơn giản này lại đem tới khả năng ứng dụng tuyệt vời, vì "chỗ trống" này có thể là mọi thứ: class, summary, sentiment, code.

Bonus: Các LLMs ngày nay được xây dựng trên mô hình Transformer, được giới thiệu bởi Google vào năm 2017. Transform dựa vào cơ chế attention để xử lý các dữ liệu đầu vào, cơ chế này cho phép mô hình tập trung vào các phần quan trọng của dữ liệu input, bỏ qua các phần kém quan trọng, giúp giảm resource cần để train và inference.

Xem thêm: [What is genetive AI](obsidian://opengate?url=https://research.ibm.com/blog/what-is-generative-AI)
### Context và parameter là gì?

![[Pasted image 20231120103134.png]]

Ngắn gọn thì context là ngữ cảnh được cung cấp bởi input, như trong ví dụ dưới đây:

"Anh ấy đang ở ..."

Câu này cung cấp rất ít nội dung liên quan tới từ còn trống, bạn bắt đầu tự assume một số ngữ cảnh trong đầu, và với từng ngữ cảnh đó, bạn liên hệ với những từ ngữ khác nhau, và kết quả có thể có rất nhiều sai khác với ý muốn của tác giả.

Nhưng nếu bạn được cung cấp nhiều context hơn, ví dụ như:

"Anh ấy đang ở _ _ _ , vì hôm nay là ngày học đầu tiên sau kỳ nghỉ hè."

Giờ câu này dễ đoán trúng hơn một chút, ta có thể liên tưởng, nghỉ hè và ngày học, khả năng anh ấy đang ở *trường*.

Trong ví dụ này, context chính là ngữ cảnh mà đoạn input cung cấp cho bạn, nó cho bạn giới hạn và direction để từ đó phát triển ra các kết quả.

Và yếu tố thứ hai là khả năng hiểu biết ngôn ngữ của bạn, bạn phải hiểu "Anh ấy", "nghỉ hè", "ngày học", "đầu tiên" là gì và có liên quan gì tới nhau từ đó tìm ra được liên quan tới "trường". Có thể hiểu nôm na rằng số lượng khía cạnh mà bạn có thể xử lý được gọi là parameter, hiểu nôm na thì nó là một đơn vị dùng để nhớ của model, càng nhiều parameter thì model có thể chứa được nhiều thông tin và pattern phức tạp hơn.

Tăng số lượng parameter đòi hỏi tốn nhiều compute hơn, tăng số lượng context đòi hỏi nhiều memory hơn[^1]. Nhưng nó cũng giúp giảm thiểu sự nhầm lẫn và tăng độ chính xác của kết quả.

### Hallucination

Một trong những vấn đề lớn nhất của AI là ảo giác, AI có thể tạo ra nội dung có vẻ rất thuyết phục, rất tự tin và chắc chắn, nhưng thực tế lại sai. Hiện tượng này gọi là ảo giác.

Nguyên nhân của ảo giác này là do dữ liệu train chứa thông tin sai lệch, không đủ đa dạng, chứa bias, thiết kế của model chưa tốt.

Trong thời kì đầu của Gen AI, kết quả ảo giác xảy ra thường xuyên hơn, về sau đã được cải thiện nhiều.

![[Pasted image 20231206104651.png]]
> nguồn: [nguoonf](obsidian://opengate?url=https://promptengineering.org/measuring-how-much-leading-ai-chatbots-hallucinate/)

Xem thêm: [[Vectara's Evaluation Approach]]

Trong các usecase sau đây, bạn sẽ có thể để ý rằng, có rất nhiều trường hợp, AI generate ra kết quả sai, code không chạy được hoặc tệ hơn là sai logic nhưng vẫn rất tự tin. Nên phải lưu ý đặt biệt khi sử dụng gen AI là phải luôn nghi ngờ.

Ở phía sử dụng, có một số cách để giảm thiểu hiện tượng ảo giác là ReACT và RAG. Hiểu điều này để ta có thể chủ động và bớt thất vọng khi sử dụng AI. Trong các ví dụ dưới đây, bạn sẽ nhận thấy rằng kết quả sẽ tốt hơn nhiều khi ta cung cấp nhiều context, prompt tố hơn. 

## Chúng ta gặp phải những thách thức gì trong lập trình?

Ta có rất nhiều vấn đề với việc lập trình, nó luôn là như thế. Đó là một phần lý do mà mỗi ngày đều có những thay đổi mới, từ ngôn ngữ lập trình, tooling, framework, service, ....

![[Pasted image 20231113103426.png|https://www.youtube.com/watch?v=JhCl-GeT4jw&ab_channel=CS50]]

**Hai điều khó chịu khi code là quá nhàm chán hoặc quá "khó".**

Ta thường phải viết đi viết lại những đoạn code như CRUD, data models, check error, gọi chung là boilerplate code, nó khá nhàm chán (rote busywork) và đôi khi khó bảo trì.

**Khó** ở đây không có nghĩa là thử thách, mà là cái khó không đáng có, xảy ra trong quá trình hiểu requirement hoặc giao tiếp. Mất nhiều thời gian để hiểu câu từ trong các cuộc họp refine, để hiểu cách hành văn yếu kém trong tài liệu. Làm sao code được khi không thể xác định đúng yêu cầu?

Tất cả những rào cản(roadblocks) này tạo ra ảnh hưởng tiêu cực lên productive, code quality, maintainability, và còn làm bớt đi hứng thú, đam mê trong lập trình.

Có lẽ, trải nghiệm lập trình sẽ không bao giờ trở nên hoàn hảo, không một ngôn ngữ nào là vừa ngọt ngào lại mạnh mẽ. Trong khi đó, Với sự tiến bộ của AI, hy vọng có thể thấy được những cải tiến thực sự trong lĩnh vực này.
### LLMs có thể giúp chúng ta giải quyết những thách thức này như thế nào?

Như đã đề cập ở trên, LLMs hiện tại có thể hiểu ngữ cảnh và generate ra mọi thứ còn để trống. Vậy nó sẽ có thể giúp ta những gì trong lập trình? Trong bài này ta sẽ điểm qua một số usage điển hình như:

1. Generate code: bao gồm generate code, comment, doc, test, 
2. Phân tích yêu cầu và consult
3. Hỗ trợ khi làm việc với các dự án cũ
4. Phân tích database
5. Onboarding và training
6. Đảm bảo coding convention

Sau đó sẽ cùng nhau nhìn lại một lần nữa về các giới hạn, cũng như lạm dụng AI.

## Structure of the article and Demonstration

To make the examples more vivid and realistic, throughout the following use cases, I will use a single example. The ultimate goal is to build a software to display stock prices on the menubar of a Mac. The project will use stacks that I am not familiar with to emphasize the support capabilities of AI.

However, there are some use cases that cannot be present in a new project: analyzing old documents, legacy code.

Repo: https://github.com/nguyenvanduocit/stock-bar
## AI hỗ trợ viết, phân tích story

### Vấn đề

User story tốt là rất quan trọng trong thành công của sprint, nhưng có hai rắc rối phổ biến:

1. User stories kém chất lượng: Nó có thể thiếu chi tiếc hoặc thậm chí là dẫn cắt developer đi theo những hướng sai lầm.
2. Đọc hiểu: Developer thiếu kinh nghiệm về sản phẩm hoặc giới hạn về góc nhìn có thể không hiểu hết hoặc hiểu sai về một story.

Có nhiều lý do cho các vấn đề trên, có thể do thiếu kiến thức về dự án hoặc thiếu kỹ năng diễn đạt, hạn chế về thời gian. Song, dù là vì yếu tố nào, thì làm sao ta có thể làm tốt nếu không hiểu được story, có thể dẫn tới việc phải làm lại từ đầu hoặc khó khăn khi làm việc với các developer khác.

### Giải pháp

Trong trường hợp này, AI thể hiện một số khả năng rất hứa hẹn như:

- Hỗ trợ viết story tốt hơn, kiểm tra chính tả, giải thích các khái nhiệm, đảm bảo convention.
- Phân tích requirement, kết hợp với hệ thống hiện có, giúp validate tính đúng đắng của story.
- Giúp developer phân tích, giải thích các khái niệm, mục đích của người viết story.


![](https://www.youtube.com/watch?v=IhHkMyxxFh8&t=63s&ab_channel=Atlassian)

Như ta thấy trong video, AI có thể giúp cho việc viết và hiểu story trở nên đơn giản hơn cho cả team. 

Product này của Atlassian chỉ mới chấp nhận cho dùng thử ở một số người trong whitelist. Tuy nhiên hãy tưởng tượng nó có thêm một số feature khác nữa như có thể tích hợp với code base trên gitlab, nó có thể tự break subtask cho developer, tự ask những câu hỏi followup, brain storm cùng với PO, tự suggest một số vấn đề có thể xảy ra, .... hoặc tự viết test case. 

### Demo

Cách tốt nhất có thể sử dụng ở hiện tại là sử dụng Github Copilot Chat. Hiện tại đã hỗ trợ JetBrain's IDE và trên VS Code.

AI cũng có thể giúp viết lại idea cho nó gọn, dễ hiểu hơn như trong ví dụ sau:


![](https://youtu.be/NpD83elT_5E)

View file: [idea.md](https://github.com/nguyenvanduocit/stockbar/blob/main/docs/idea.md)

Từ đây ta sẽ yêu cầu AI tạo requirement dựa trên ideal này.

![](https://youtu.be/gJxTNwxt9ao)

View file: [requirement.md](https://github.com/nguyenvanduocit/stockbar/blob/main/docs/requirement.md)

Dựa vào requirement này ta generate ra user story và task như sau:

![](https://youtu.be/7eWjXZ8ARcI)

View file: [user-stories.md](https://github.com/nguyenvanduocit/stockbar/blob/main/docs/user-stories.md)

## AI giúp thiết kế kiến trúc hệ thống

### Vấn đề

Thiết kế kiến trúc hệ thống là một quá trình quan trọng và phức tạp, đòi hỏi kiến thức chuyên môn sâu rộng và kỹ năng đưa ra quyết định sắc bén. Kiến trúc hệ thống cần đáp ứng các yêu cầu về hiệu năng, an ninh, linh hoạt và khả năng mở rộng. Đồng thời, kiến trúc hệ thống cần phù hợp với đặc thù của doanh nghiệp, có thể thích ứng với những thay đổi về yêu cầu và có thể tích hợp chặt chẽ với hệ thống cũ.

### Giải pháp

Ứng dụng AI trong thiết kế kiến trúc hệ thống có thể giúp ích rất nhiều, giống như việc tìm kiếm thông tin trên Google hoặc đọc sách, nhưng trực tiếp và tiết kiệm thời gian hơn. Dưới đây là một số cách mà AI có thể giúp ích:

1. **Đưa ra các gợi ý thiết kế**: AI có thể phân tích các yêu cầu và đánh giá các lựa chọn khác nhau để đưa ra các gợi ý thiết kế phù hợp nhất với nhu cầu của doanh nghiệp. Điều này giúp các nhà phát triển hệ thống tiết kiệm thời gian và công sức.
2. Tạo ra các biểu đồ cần thiết để giúp hiểu rõ hơn về hệ thống: Dựa trên các yêu cầu, AI có thể tạo ra các biểu đồ cần thiết để giúp hiểu rõ hơn về hệ thống, chẳng hạn như biểu đồ luồng dữ liệu (data flow diagram) hoặc biểu đồ trình tự (sequence diagram). Điều này giúp các nhà phát triển hệ thống dễ dàng nắm bắt và quản lý hệ thống.
3. Tìm ra các rủi ro tiềm ẩn và đề xuất các chiến lược giảm thiểu: AI có thể giúp tìm ra các rủi ro tiềm ẩn và đề xuất các chiến lược giảm thiểu.

Có nhiều level architecture ([[software architecture level]]). 


### Demo AI giúp thiết kế hệ thống phần mềm




### Demo Draw diagram

Mình nhận thấy bản thân là visual person, việc vẽ, viết ra giúp mình hoàn thiện các suy nghĩ. Và cũng là một output không thể thiếu của quá trình design. Nhưng nó không nhất thiết là bạn phải tự mình vẽ toàn bộ, AI có thể giúp init một số diagram đơn giản để từ đó ta tập trung vào các phần thú vị hơn. Như trong ví dụ dưới đây, mình gọi AI vẽ cho mình từng bước một, đầu tiên vẽ sự tương tác giữa collector và database, sau đó tương tác của database với analysis. 

![[Pasted image 20231121165252.png]]
Kết quả sẽ càng sát với yêu cầu khi bạn cung cấp cho nó càng nhiều context. Tool mà mình sử dụng ở đây là usediagram.com của bạn @hey_thien phát triển. Mỗi khi bạn input yêu cầu vào, tool sẽ generate ra code staruml để thể hiện diagram, bạn có thể sửa đổi cả code này hoặc yêu cầu, giúp kết quả generate thêm chính xác. Việc này cũng chính là bạn đang cung cấp nhiều context cho nó hơn.

Đã thiết kế xong, phần tiếp theo ta cần hiện thực các design này thành từng dòng code cụ thể. Việc mà qua thời gian có phần trở nên nhàm chán, và hằng ngày ta luôn tìm cách để cải thiện nó.

## Code Generation

Khi code, ta sử dụng thứ ngôn ngữ kỳ lạ mà con người không sử dụng, một loại thần chú bí ẩn, chắc chắn là nó không hề thoải mái, từ xưa:

![[Pasted image 20231121171409.png]]

cho đến nay:

![[Pasted image 20231121171428.png]]

Một cái khó khác nữa là boilerplate code. 

![img.png](img.png)

Dễ thường trong codebase có rất nhiều dòng như thế này:

![[Pasted image 20231121172916.png]]

Nó lặp đi lặp lại, và ... nhàm chán.

Để giải quyết vấn đề này, chúng ta đã đi tìm nhiều giải pháp, một số ngôn ngữ lập trình hỗ trợ macro (rust), trait (PHP), IDE thì hỗ trợ giao diện kéo thả, auto complete, bí quá thì ta lại dùng snippet.

Tuy nhiên, những thứ trên có vẻ vẫn chưa thỏa mãn lắm, nó vẫn để lại những dòng thần chú lặp đi lặp lại, phải động não thì mới hiểu được.

Với AI thì có chút khác biệt, không còn phải lưu một đống snippet dài nữa, nhớ lại lần đầu tiên sử dụng copilot, khi viết một comment bằng tiếng người, và thần chú được tạo ra, nếu không muốn kết quả đó thì có thể tìm kết quả khác, ngay trực tiếp trên file code đang làm, rất tiện.

Nhưng ngày nay nó còn mạnh mẽ hơn nữa khi bạn không còn cần phải chọn những kết quả khác nhau nữa, mà có thể trực tiếp cung cấp thêm context lại cho copilot để generate ra đoạn code mới gần với mong đợi hơn.

![](https://youtu.be/C9Dwm8caoU8)

Một prompt rất kì cục, nhưng khi được cung cấp rất nhiều context, như vị trí chuột, các file đang mở, hoặc thậm chí có thể upload file lên, Copilot có thể generate ra câu trả lời rất chính xác.

Một vấn đề nữa của boilerplate code là khó bảo trì, dù nó cần ít nỗ lực hơn là kế thừa, nhưng khi cần thay đổi một logi nào đó thì lại phải đi tìm và sửa ở mọi chỗ. Cũng không quá khó nếu ta dùng search/replace. nhưng đôi khi boilerplate cần sửa lại chút ít, thì lúc này chỉ có AI mới giúp tìm ra được, AI có thể process toàn bộ codebase tìm ra những đoạn giống nhau và sửa đồng loạt.

Có nhiều level generate code. nếu ở ví dụ trên ta generate từ dòng code cho backend, thì dưới đây ta có thể generate ra các component cho frontend:

![](https://youtu.be/WbUF6XEk0zI)

Bonus một số tool generate:

1. https://tailwind-ai-generator.vercel.app/tailwind/860
2. https://flutterflow.io/ai-gen
3. https://retool.com/products/ai

## AI giúp viết test

Thú thật mình rất rất ít khi viết unittest, nó khá là mất thời gian và khó nữa, chỉ viết khi function đó thực sự quan trọng và khó integration test. Mình tin là cũng có nhiều developer như thế.

Nhất là với TDD, chúng ta phải xác định rõ những gì ta mong đợi trước khi code, đúng, đó là điều nên làm. Nhưng thành thật với bản thân, thì phải estimate thêm 50% nữa thì mình mới dám thực hành TDD.

Unittest cũng giống như bảo hiểm vậy, ta chỉ thấy giá trị của nó khi có bug xảy ra, còn khi mọi thứ ổn thì ta gần như không thấy lợi ích của nó. Tuy nhiên unittest là best practice và là yêu cầu, tiêu chuẩn trong các enterprise application. 

Xưa có câu: Phàm việc gì ta không muốn làm, thì hãy để cho AI làm.

![[Pasted image 20231114135420.png]](https://www.toptal.com/qa/how-to-write-testable-code-and-why-it-matters)

Như bạn thấy trong demo, việc viết unittest giờ đơn giản hơn trước rất nhiều, dù rằng cũng có một số hạn chế, nhưng đó là điều chấp nhận được và nên làm. Vậy nên với sự giúp đỡ của AI, mong là việc áp dụng TDD sẽ đơn giản và được adapt nhiều hơn.

![](https://youtu.be/HFJlTDE_vLA)

Dù vậy, để làm ví dụ này, không ít lần nó generate ra những case không cần thiết, ví dụ custom protocol.
## AI giúp viết doc

Thường thì ta viết code giỏi hơn viết doc, mặc dù viết doc là một kỹ năng quan trọng. Cũng giống như Unittest, trong quá trình làm việc, ta không cần doc cho những gì ta đã làm, nhưng chỉ khi cần đọc ta mới thấy giá trị. Vì vậy ta cũng thường không xem trọng nó, nhưng nó cũng một lần nữa, là best practice, và là policy trong các enterprise application. Hơn nữa viết doc cũng giúp ta tự review lại hệ thống của mình.

Những gì ta không muốn làm, hãy để AI làm.

![](https://youtu.be/bKXGut226CA)

Quá trình viết doc này, AI không làm hoàn toàn, mà có sự hướng dẫn và review của developer, nhưng đóng vai trò là người review.

Sử dụng AI đặc biệt có lợi tron trường hợp cần phải viết doc cho dự án đã cũ, hoặc một thời gian dài không cập nhật doc. Vì AI có thể xử lý toàn bộ codebase và doc cũ cùng lúc, nhanh chóng, nên quá trình viết lại doc này sẽ đơn giản hơn. Copilot cho phép rewrite một đoạn được select, giúp chỉnh sửa nội dung đơn giản hơn.

## AI giúp viết commit

![img_1.png](img_1.png)

Nhìn vào commit này thật khó để có thể reverse lại đúng vị trí lỗi, chưa kể là có thể một commit này có thể chưa nhiều change hơn nó mô tả. Để cải thiện vấn đề này, ta có nhiều practice như converntional commit, hoặc khuyên commti liên tục và commit nhỏ. Nhưng dev mãi vẫn là dev.

Với AI, nó có thể phân tích kết quả của git diff và tạo ra nhiều command giúp phân chia các thay đổi vào đúng commit, commit với nội dung đúng hơn từ đó cho ra git tree đẹp, dễ hiểu và revserse.

![](https://youtu.be/ILFWF2eMuDY)

Trong demo này, mình đã thực hiện hai công việc khác nhau và quên commit. Github Copilot giúp mình tạo ra 2 commit riêng biệt cho từng thay đổi.

Tuy nhiên đây chỉ là một ví dụ đơn giản, hiện tại nó còn nhiều hạn chế, ví dụ nếu như bạn thực hiện hai thay đổi khác nhau trên cùng một file thì không ai có thể giúp bạn nổi. Khi AI rẻ hơn và nhanh hơn, nó chết process code của bạn realtime thì mới có thể giúp í được trong trường hợp rắc rối này.

## Review code

![[Pasted image 20231117135349.png]]

Đây là một best practice trong phát triển phần mềm, sau khi pass các testcase, lint rules thì phần logic không thể được review bằng các rule. Nhưng nó cũng là phần quan trọng trong code base. Việc review code giúp đảm bảo healthy của codebase qua thời gian[^2].

Nếu ai từng làm code review thì có lẽ sẽ đồng ý rằng review code khá khó, khó nhất là làm sao cân bằng giữa ý kiến các nhân và healthy của codebase. Chúng ta dễ thường xem những practice của bản thân là tốt hơn, và những logic ta không hiểu, hoặc rối rắm với cách ta suy nghĩ là bad. Nhưng vấn đề là đôi khi nó đúng, đôi khi nó sai.

![[Pasted image 20231115093835.png]]

AI thì không có cảm tính như vậy, dù nó có bias, nhưng ta có thể cung cấp policy của chúng ta cho nó dưới prompt để force nó follow theo, như vậy việc review sẽ bớt cảm tính hơn nhiều. Hãy xem ví dụ như dưới đây:

Mình tạo một assistant trên OpenAI. và cung cấp cho nó system prompt và một số file về code review của google[^3] để retrieval như sau:

![[Pasted image 20231115103147.png]]

Mình sẽ thử copy một đoạn text bất kỳ trên internet để nhờ nó review xem sao, trong thực tế thì ta sẽ sử dụng code changes trong commit. Mình sẽ sử dụng đoạn code sau:

```go
```go
func DiscountEdit(ctx context.Context, shopID int64, discountEdit *model.DiscountEdit, repo *repository.MongodbRepository) error {

	order, mcaDirectPurchase, err := lambda_func.GetOrderDetails(ctx, shopID, discountEdit.OrderID)
	if err != nil {
		if strings.Contains(err.Error(), "order not found") {
			return nil
		}
		return errors.Wrap(err, "failed to get order details")
	}

	sales := ConvertDiscountEditToSaleReports(*discountEdit, *order, mcaDirectPurchase)
	//if err != nil {
	//	return errors.Wrap(err, "failed to convert order refund to sale reports")
	//}
	if len(sales) == 0 {
		return nil
	}

	err = repo.SaveItemNew(ctx, sales)
	if err != nil {
		return errors.Wrap(err, "failed to insert OrderEdit to sell report")
	}
	return nil
}
```

Kết quả mà AI review là như sau:

![[Pasted image 20231115111038.png]]
![[Pasted image 20231115111238.png]]
![[Pasted image 20231115112137.png]]
Cá nhân mình thấy kết quả như vầy là rất tốt, mặc dù các tool lint là cần thiết để analyze code, nhưng nếu có thể kết hợp với AI thì kết quả sẽ đáng giá hơn. Ví dụ như trong demo này là điều mà các tool lint khó làm được:

![[Pasted image 20231115112224.png]]
Nhưng lại rất có ý nghĩa, nó nhắc ta lại về business. Liệu định nghĩa currencyRate như vậy có thực sự đúng chưa, hoặc có lẽ mục đích của ta không phải là currencyRate mà là một cái gì khác.

## AI giúp bảo trì hệ thống cũ

Có một câu nói đùa rằng chúng ta nhảy việc để trốn legacy code mình tạo ra để bơi trong legacy code mà người khác vừa nhảy đi. Nói đùa như mà cũng đúng thật, chúng ta luôn sợ legacy code, dù là của mình hay của người khác. Nhất là nếu đó là codebase bị phạm vào tất cả những điều trên, không có doc, thiết kế không rõ ràng, commit lộn xộn. 

AI có thể giúp, trường hợp này cũng giống như khi AI hỗ trợ viết doc vậy, sử dụng AI để index toàn bộ codebase, và có thể giải đáp cũng như phân tích mọi đoạn code có trong codebase, bạn hỏi nó làm cách nào để deploy, hoặc run một service, nó sẽ trả về cho bạn các command cần thiết mà không cần phải đi mò mẫm hoặc đợi hỏi người đi trước.

Song muốn được như vậy, có lẽ nó cần một giải pháp đầy đủ hơn, vì ngoài codebase, nó còn cần phải index được các requirement, issue, changelog, ...

#![](https://youtu.be/upV8znS-HU4)

Hiện tại thì chưa tiện lắm, bạn phải tự cung cấp một số file cho context, đồng thời không access được toàn bộ các tài liệu liên quan tới project cũng như codbase. Tuy nhiên, Github đang phát triển Github Copilot cho enterprise để hỗ trợ khả năng này.

## AI giúp viết command line

Viết command line có lẽ là một trong những lĩnh vực được hỗ trợ đầu tiền khi open ai ra đời. Nó không quá phức tạp như generate code, đơn giản hơn và context cũng ngắn hơn nhưng lại cấp thiết hơn, vì các terminal hầu như không hỗ trợ autocompelte như trên IDE.

![[Pasted image 20231115094106.png]]

Gần đây nhất ta có Gihub Copilot dành cho cli. nhưng nó còn đơn giản và cách sử dụng phức tạp. Warp là một terminal có feature giống như một editor, hỗ trợ AI rất smooth, hãy cùng xem trong ví dụ dưới đây.

![[demo_warp.mp4]]
Song, run cli thì bạn nên cẩn thận, vì nếu hoàn toàn không hiểu rõ command đang chạy là gì thì dễ dẫn tới sai lầm đáng tiếc, vì dụ nếu bạn bảo AI remove một thư mục nào đó và nó trả về đoạn command sau thì sẽ rắc rối:

```shell
rm -rf /
```

## Challenges and Considerations

Dù AI có những limit và tiện lợi như vậy, nhưng cũng như bao nhiêu làn sóng khác, việc sử dụng Ai và phát triển các tool hỗ trợ AI cũng gây ra nhiều tranh cãi và lo ngại.

### Lệ thuộc vào AI

**Sự phụ thuộc:** Mối quan tâm chính là developer có thể trở nên quá phụ thuộc vào AI. Sự phụ thuộc này có thể làm developer càng ngày càng kém kỹ năng viết code, vì developer có thể dựa vào các đề xuất của AI mà không hiểu logic cơ bản.

**Mất tính sáng tạo:** Việc phụ thuộc nhiều vào AI để code có thể hạn chế khả năng sáng tạo của developer. Các giải pháp do AI đưa ra có xu hướng dựa trên các pattern hiện có, nếu developer chỉ hài long với kết quả đó thì có thể cản trở việc tạo ra các giải pháp mới.

### Bảo mật và riêng tư

Một vấn đề khác là vấn đề bảo mật, có nhiều level cho concern này, khi cả code base được index và gửi lên server của OpenAI, không chắc rằng nó có bị đem đi sử dụng vào mục đích khác hay không. Với lo ngại này, nhiều công ty hướng tới sử dụng các model open source và xây dựng các policy trong việc sử dụng AI. 

Ngoài ra, AI có thể bị inject, ví dụ bạn parse nội dung của một website, và website đó âm thầm chèn vào một số đoạn nhằm inject context không phù hợp vào prompt của bạn, khiến AI đưa ra những kết quả không mong muốn.

Khi AI bùng nổ, mọi công ty đều muốn chia phần, nhiều công ty bất chấp privacy của người dùng, có thể sử dụng dữ liệu của người dùng để train cho model của họ, những thông tin này có thể được generate cho các user khác. Dẫn tới nhiều lo ngại về privacy.

## Cái nhìn vê tương lai

Một trong những yếu tố giới hạn LLMs hiện tại có lẽ là compute, các mô hình này đều đòi hỏi lựa phép tính khổng lồ để train, fine-tune và inference. Nên hiện tại vẫn chưa thể có một model có thể xử lý dữ liệu và update model realtime.

Nhưng với sự phát triển và đầu tư hiện tại, các giới hạn này bị phá vỡ mỗi ngày, về cả độ lớn của model lẫn các kỹ thuật finetune, tối ưu resource. Các công ty về hardware cũng có những cải tiến của mình.

Dù muốn dù không, sự phát triển của AI là điều không thể tránh khỏi được, khi một cái gì mới phát triển, nó sẽ sẽ thay thế dẫn cái cũ, và có lẽ cách chúng ta lập trình trong 2 năm nữa sẽ rất khác với cách ta đang code hiện tại. Sự thích ứng là điều bắt buộc, nhưng nó không có nghĩa là làm lụt đi kỹ năng của mình, thay vào đó, hãy vẫn tập luyện cho đôi cánh của mình và đính vào đó những công cụ phù hợp để banh nhanh hơn, cao hơn.

Đối với doanh nghiệp, nên có cái nhìn tích cực và đầu tư nhiều hơn vào AI song song với phát triển những skill mới cho nhân viên. Bằng việc tái cấu trúc mình của Github, hướng hoàn toàn vào AI, cũng như xu thế của các công ty FANG, ta có thể thấy rằng AI sẽ là một trong những yếu tố quan trọng để cạnh tranh trong tương lai. Chậm bước trong lĩnh vực này có thể làm mất đi nhiều lợi thế. Ứng dụng tốt và đúng AI vào workflow hằng ngày có thể đem lại cải tiếng đáng kể. Song song với đó là phát triển policy để đảm bảo các vấn đề về bảo mật, riêng tư.

## Conclusion

Trong bài này, ta hiểu hơn về Gen AI và một chút khái niệm về context và parameter. Ta có thể thấy, đôi khi, mục tiêu đơn giản lại có thể đem lại những ứng dụng rộng rãi. Nhưng giới hạn của nó là sử dụng quá nhiều tài nguyên, và output còn nhiều ảo giác, bias. Nhưng với sự phát triển và đầu tư hiện tại, các giới hạn này bị phá vỡ mỗi ngày. Tươi lai của một ngôn ngữ lập trình tự nhiên, có khả năng tự sửa mình là không xa lắm. AI sẽ là một bước thay đổi mà không ai có thể đứng ngoài được.

![[Pasted image 20231121171845.png]]

## Footnotes

[^1]: [Scaling Laws of Large Language Models: Parameters vs Tokens - Sarvex Jatasra
](https://www.linkedin.com/pulse/scaling-laws-large-language-models-parameters-vs-tokens-jatasra-p0ogf/)
[^2]: [Google Eng Practice](https://google.github.io/eng-practices/)
[^3]: [Styleguide repo](https://github.com/google/styleguide)
