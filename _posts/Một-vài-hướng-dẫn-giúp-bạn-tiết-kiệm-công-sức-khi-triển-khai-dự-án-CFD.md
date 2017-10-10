
title: "Tối ưu thời gian cho dự án CFD của bạn qua một vài bước đơn giản"
sub_title: "Best CFD Practise Guide"
categories:
  - CFD
  - Practise Guide
elements:
  - Math Equation
  - css
  - formatting
  - html
  - markup
last_modified_at: 2017-10-10T00:33:59-05:00


Tôi chắc rằng hầu hết các bạn làm mô phỏng đã từng trải qua cảm giác lo lắng khi chương trình bắt đầu chạy dù cho trước đó bạn đã dành rất nhiều thời gian cho việc dựng mô hình, chia lưới, set điều kiện biên và solver. 

*Rất nhiều trường hợp có thể xảy ra! Liệu rằng chương trình có bị dừng ngay tức khắc hay là nó lỗi khi đã hoàn thành 70, 80% thậm chí là 96%? Chương trình sẽ chạy mất bao lâu, 1 giờ, 2 giờ hay vài ngày và nằm ngoài dự tính của bạn?*

Thực ra điều đó là hoàn toàn bình thường khi bạn làm CFD. Theo thời gian, khi bạn tích lũy được nhiều kinh nghiệm, bạn hoàn toàn có thể hạn chế được các rủi ro đó, hay nói cách khác là bạn có thể kiểm soát được các yếu tố trong một dự án mô phỏng. 

Vậy còn đối với các bạn có ít kinh nghiệm hoặc mới tiếp xúc với các bài toán CFD, làm sao để hạn chế điều đó. Hướng dẫn sau đây có thể sẽ giúp ích cho bạn.

### 1. Kiểm tra kĩ lưỡng các thiết lập

Sau khi bỏ rất nhiều công sức cho việc xây dựng mô hình, chia lưới và thiết lập ... có lẽ cái cảm giác ấn nút (hoặc gõ lệnh) để cho chương trình chạy rồi ngồi đợi kết quả sẽ rất cuốn hút bạn. Tôi thường xuyên trải qua cảm giác đó. Tuy nhiên, chỉ một thao tác nhầm lẫn có thể khiến bạn mất nhiều công sức để rà soát lại từ đầu xem lỗi phát sinh từ đâu. Nó khiến bạn mệt mỏi hơn khi quá trình này cứ lặp đi lặp lại, hoặc tệ hơn là khi chạy được 99% thì bạn nhớ ra là bạn đã thiết lập sai 1 thông số nào đó. Do vậy, ***lời khuyên đầu tiên dành cho bạn là luôn kiểm tra thật kĩ mọi thiết lập trước khi chạy***. Tốt nhất là bạn hãy lập ra 1 danh sách các thông số quan trọng bao gồm:
    1. Mô hình:
        * Kiểm tra đơn vị: inch, meter hay mm? Tôi từng mất vài ngày để tìm ra lỗi sai của chương trình chỉ vì không thống nhất đơn vị của mô hình và solver. Điều này rất dễ xảy ra khi bạn sử dụng các phần mềm của các hãng khác nhau trong các công đoạn trong 1 project. 
        * Kiểm tra mô hình và bản vẽ: 