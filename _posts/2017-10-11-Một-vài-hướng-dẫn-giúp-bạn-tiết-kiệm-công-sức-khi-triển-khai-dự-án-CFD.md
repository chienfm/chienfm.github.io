---
title: "Tiết kiệm thời gian cho dự án CFD của bạn qua một vài bước đơn giản"
excerpt: "Bài viết này đưa ra một vài lời khuyên cho các bạn mới tìm hiểu về mô phỏng"
header:
  overlay_color: "#333"
categories:
  - CFD
tags:
  - CFD
  - Practise Guide
last_modified_at: 2017-10-17T15:55
---

Có lẽ hầu hết các bạn làm mô phỏng đã từng trải qua cái cảm giác lo lắng khi chương trình bắt đầu chạy dù cho trước đó bạn đã dành rất nhiều thời gian cho việc dựng mô hình, chia lưới, chọn solver và đặt điều kiện biên. 
{: .text-justify}

<q>Rất nhiều trường hợp có thể xảy ra! Liệu rằng chương trình có bị dừng ngay tức khắc hay là nó lỗi khi đã hoàn thành 70, 80% thậm chí là 96%? Chương trình sẽ chạy mất bao lâu, 1 giờ, 2 giờ hay vài ngày và nằm ngoài dự tính của bạn?</q>
{: .text-justify}

Thực ra điều đó là hoàn toàn bình thường khi bạn làm CFD. Theo thời gian, khi bạn tích lũy được nhiều kinh nghiệm, bạn hoàn toàn có thể hạn chế được các rủi ro đó, hay nói cách khác là bạn có thể kiểm soát được các yếu tố trong một dự án mô phỏng.
{: .text-justify} 

Vậy còn đối với các bạn có ít kinh nghiệm hoặc mới tiếp xúc với các bài toán CFD, làm sao để hạn chế điều đó. Hướng dẫn sau đây có thể sẽ giúp ích cho bạn.
{: .text-justify}
{% include toc icon="gears" title="My Table of Contents" %}
### 1. Kiểm tra kĩ lưỡng các thiết lập

Sau khi bỏ rất nhiều công sức cho việc xây dựng mô hình, chia lưới và thiết lập... có lẽ cái cảm giác ấn nút (hoặc gõ lệnh) để cho chương trình chạy rồi ngồi đợi kết quả sẽ rất cuốn hút bạn. Mình thường xuyên trải qua cảm giác đó. Tuy nhiên, chỉ một thao tác nhầm lẫn có thể khiến bạn mất nhiều công sức để rà soát lại từ đầu xem lỗi phát sinh từ đâu. Nó khiến bạn mệt mỏi hơn khi quá trình này cứ lặp đi lặp lại, hoặc tệ hơn là khi chạy được 99% thì bạn nhớ ra là bạn đã thiết lập sai 1 thông số nào đó. Do vậy, <span style ="color:blue">*lời khuyên đầu tiên dành cho bạn là luôn kiểm tra thật kĩ mọi thiết lập trước khi chạy*</span>. Tốt nhất là bạn hãy lập ra 1 danh sách các thông số cần quan tâm. Nó có thể bao gồm:
{: .text-justify}
  * Mô hình (Geometry):
    * Đơn vị: inch, meter hay mm? Mình từng mất vài ngày để tìm ra lỗi sai của chương trình chỉ vì không thống nhất đơn vị của mô hình và solver. Điều này rất dễ xảy ra khi bạn sử dụng các phần mềm của các hãng khác nhau cho mỗi công đoạn trong project.
    {: .text-justify}

    * Tính chính xác của bản vẽ: Điều này thường ít xảy ra nhưng đôi lúc lại rất nghiêm trọng. Nhiều tip mô phỏng dạy bạn cách giảm bớt sự phức tạp của mô hình bằng cách bỏ qua một vài góc lượn hoặc chi tiết. Phương pháp này hữu ích khi bạn hiểu rõ tính chất vật lý/hiện tượng của phương pháp mô phỏng bạn đang áp dụng. Ngược lại, nó có thể khiến kết quả mô phỏng bị sai lệch. Tất nhiên, bạn hoàn toàn có thể đánh giá sai lệch này để rút ra kinh nghiệm cho các project tương tự. Điều này giúp bạn cân bằng giữa sai số và tính phức tạp của mô hình và kiểm soát trong giới hạn cho phép.
    {: .text-justify}

  * Chia lưới (Meshing):
    * Chọn kích thước phần tử: khi bạn bắt đầu làm quen với CFD, hãy luôn tập cho mình thói quen kiểm tra sự độc lập của kích thước phần tử với kết quả mô phỏng. Với cùng một mô hình, hãy tạo ra ít nhất 3 kích thước khác nhau để kiểm chứng. Điều này có thể rất mất thời gian nhưng lại rất hữu ích. Hãy nhớ, mục đích của các phương pháp CFD là tính chính xác chứ không phải chỉ là màu sắc rất đẹp hiển thị trên màn hình.
    {: .text-justify}

  * Solver:
    * Loại biên (boundary type): chọn cho mình loại biên phù hợp với điều kiện vật lý và các thiết lập đi kèm là rất quan trọng với một bài toán CFD. Điều này chỉ có thể tích lũy qua việc tham gia các bài giảng, tutorial, training ... và nếu một điều kiện biên nào đó không có sẵn thì bạn có thể tự viết riêng cho mình (phần này có thể mình sẽ đề cập trong 1 chuyên đề khác).
    {: .text-justify}

    * Điều kiện đầu (Initial condition) và thông số biên (boundary condition): Hãy luôn chắc rằng bạn đã thiết lập đúng các giá trị, đơn vị. Chắc hơn, hãy kiểm tra một vài lượt trước khi chạy mô hình.
    {: .text-justify}
    * Scheme and Solution: phần này khá chuyên sâu, mình sẽ cập nhật nội dung hoặc viết riêng 1 topic khác.
    {: .text-justify}

### 2. Từ đơn giản đến phức tạp

* Khi bắt đầu với 1 bài toán CFD, việc chia nhỏ tính toán thành các bước sẽ khá hữu ích. Với các mô hình phức tạp, mình thường đơn giản hóa để kiểm tra các thiết lập. VD, khi mô phỏng 1 kho lạnh với rất nhiều hàng hóa, thay vì xây dựng trực tiếp mô hình, mình tạo ra 1 phòng nhỏ chứa một vài đối tượng với đầy đủ các điều kiện biên tương tự. Điều này giúp mình nhanh chóng kiểm tra và thay đổi các thông số. Nó đặc biệt hữu ích khi mô hình của bạn có thể có tới vài chục triệu cell. Một ví dụ khác, khi mô phỏng thiết bị trao đổi nhiệt, thay vì áp cả 2 điều kiện biên là nhiệt độ và lưu lượng cùng lúc, mình chỉ chạy mô hình với lưu lượng mà bỏ qua trao đổi nhiệt. Các thông số khác sau đó được thêm vào theo mức độ phức tạp tăng dần như nhiệt độ đầu vào phụ thuộc hay biến thiên theo thời gian, độ nhớt chất lưu thay đổi theo nhiệt độ v.v...
{: .text-justify}
* Thường khi mới làm quen với CFD, bạn sẽ rất nóng lòng được thử sức với những bài toán thực tế. Nhưng đôi khi vấn đề lại khá phức tạp vì nó có thể là tập hợp của nhiều hiện tượng vật lý. Do vậy hãy kiên trì theo từng bước, từ đơn giản đến phức tạp, phân tách hiện tượng ra các khối nhỏ để dàng mô phỏng và đánh giá kết quả. Mình tin rằng, điều đó sẽ rất hữu ích và tiết kiệm thời gian của bạn.
{: .text-justify}

### 3. Tham khảo hướng dẫn đi kèm phần mềm

* Hãy luôn tham khảo hướng dẫn từ nhà sản xuất hoặc tác giả của phần mềm bất cứ khi nào bạn lựa chọn 1 thiết lập. Ngành CFD đã có 1 lịch sử phát triển khá dài cộng với việc mỗi phần mềm được phát triển với sự đóng góp của rất nhiều chuyên gia, do đó, hiểu được ý nghĩa thông số mình định sử dụng sẽ giúp ích rất nhiều.
{: .text-justify}
* Ngoài ra, một vài phần mềm mô phỏng có đi kèm các công cụ phân tích để đưa ra lời khuyên cho người dùng khi sử dụng các thiết lập. Hãy tận dụng điều đó.
{: .text-justify}

### 4. Tham khảo ý kiến chuyên gia, người có kinh nghiệm

Nếu bạn bế tắc cả tháng trời mà không tìm ra phương pháp, hãy thử tham khảo ý kiến của các chuyên gia hoặc người có kinh nghiệm trong lĩnh vực bạn làm mô phỏng. Sự thực là có đôi lúc kiến thức về cơ học và phương pháp số sẽ là "chưa đủ" khi bạn làm việc với các phần mềm mô phỏng thông dụng hiện nay. Một vài chỉ dẫn sẽ đặc biệt hữu ích với bạn lúc này. Bạn cũng có thể tham gia các buổi training của hãng để có thể làm chủ được các thiết lập sâu hơn.
{: .text-justify}

### 5. Just Relax

Đôi lúc bạn bỏ rất nhiều thời gian mà chương trình chạy không như mong muốn. Hãy nghỉ ngơi, uống 1 cốc cafe, xem một bộ phim hay chơi một ván game. Khi quay lại đột nhiên bạn sẽ nhận ra điểm sai sót của mình.
{: .text-justify}


<kbd>Kiên trì và tỉnh táo, bạn sẽ thành công trong thế giới CFD.</kbd>
{: .text-justify}
