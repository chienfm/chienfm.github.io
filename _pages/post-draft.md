---
layout: single
title:  "CFD - Phương trình cơ bản 1"
permalink:  /draft1/
categories: 
  - CFD
tags:
  - CFD
last update: 2017-10-28T17:46
---
Các biến của phương pháp cơ học tính toán, dù ở dạng nào, đều được dựa trên các tính chất cơ bản của cơ học chất lỏng bao gồm `tính liên tục (continuity)`, `động lượng (momentum)` và `năng lượng (energy)`. Chúng được khái quát hóa bằng các định luật toán học cơ bản sau:
  - Định luật bảo toàn khối lượng.
  - Định luật 2 Newton $F = ma$.
  - Định luật bảo toàn năng lượng.
{: .text-justify}

Trong chương này, chúng ta sẽ cùng thực hiện các biến đổi để xây dựng ra các phương trình đặc trưng cũng như sẽ cùng thảo luận để hiểu kĩ hơn về tính chất và ý nghĩa của chúng. Hiểu rõ cách xây dựng và ý nghĩa của phương trình giúp bạn nắm rõ cách vận dụng và có thể tự phát triển các công cụ tính toán sau này.
{: .text-justify}

## 1. Mô hình hóa dòng chất lưu

Khi xem xét một khối rắn trong chuyển động tịnh tiến, chúng ta thấy rằng vận tốc của mọi phần của khối này là như nhau. Tuy nhiên, đối với chuyển động của khối chất lưu, vận tốc của mỗi phần trong khối này có thể không giống nhau. Vậy làm cách chúng ta có thể quan sát một khối chất lưu chuyển động rồi từ đó có thể áp dụng các định luật vật lý? Trong môi trường chất lưu liên tục, chúng ta có thể giải quyết vấn đề đó bằng cách áp dụng 1 trong 4 mô hình trình bày tiếp đây.
{: .text-justify}

### 1.1 Thể tích kiểm tra hữu hạn (Finite Control Volume)

Phần này sử dụng khái niệm `Control Volume` và `Control Surface`. Nếu các bạn đã học qua *động lực học chất lưu* thì chắc sẽ ko xa lạ với với các định nghĩa trên. Các bạn không trong chuyên ngành có thể tham khảo giải thích nhỏ trong phần `Note`. Mình thích dùng từ nguyên bản là `Control Volume` hơn, nhưng để thuận tiện và thống nhất, từ nay khái niệm này sẽ được gọi là `Thể Tích Kiểm Tra`. Ngoài ra các khái niệm khác mình cũng sẽ để chú thích tiếng Anh để các bạn thuận tiện tra cứu và dễ dàng khi đọc các tài liệu, bài báo tham khảo.
{: .text-justify}

<center>
  <figure>
    <img src="{{ site.url }}{{ site.baseurl }}/assets/images/CFD/Model_of_flow.png" alt="Mô hình hóa dòng chảy" width="370" height="300">
    <figcaption>Hình 1. Mô hình hóa dòng chất lưu.</figcaption>
  </figure>
</center>

Trước hết, ta xem xét một trường dòng (`flow field`) tổng quát trong `Hình 1.a` và `Hình 1.b)` . Trong hình, ta có *thể tích kiểm tra* $\mathscr{V}$, *mặt bao thể tích kiểm tra S* (`control surface`) và các *đường dòng* (`streamlines`). *Thể tích kiểm tra* có thể cố định trong không gian với chất lưu di chuyển qua nó như *Hình 1a* hoặc chuyển động với đường dòng như trong *Hình 1.b*. Trong cả hai trường hợp, thể tích kiểm tra được giả sử là đủ lớn, chiếm một thể tích hữu hạn trong dòng chất lưu. Các mô hình sẽ được áp dụng trên *thể tích kiểm tra* thay vì áp dụng trên cả *trường dòng*. Các phương trình của dòng chất lưu được khai triển trực tiếp bằng cách áp dụng các định luật vật lý và khi đó sẽ ở dạng *tích phân*. Dạng tích phân của các *phương trình điều khiển* (`Governing Equation`) này cũng có thể biến đổi qua hệ *phương trình vi phân* một cách gián tiếp. Sự khác biệt giữa hai trạng thái trong hình `1.a` và `1.b` là ở chỗ, dù biểu diễn dưới dạng tích phân hay vi phân thì phương trình điều khiển cho trường hợp `1.a` sẽ có dạng *bảo toàn* (`Conservation form`), còn trường hợp `1.b` sẽ có dạng không bảo toàn (`nonconservation form`). Chúng ta sẽ giải thích rõ hơn điều này khi thực hiện biến đổi toán học ở các phần tiếp theo.
{: .text-justify}

### 1.2 Phần tử chất lưu hữu hạn (Infinitesimal Fluid Element)

Tiếp tục xem xét trường dòng cho các trường hợp `1.c` và `1d`. Giả sử chúng ta có các phần tử chất lưu vô cùng nhỏ với các thể tích khác nhau $\mathscr{dV}$ trong dòng chất lưu. Lưu ý là các phần tử này dù nhỏ nhưng vẫn vô cùng lớn so với kích thươc phân tử. Do đó ta vẫn có thể coi đây là một môi trường liên tục. Và tương tự như trường hợp của thể tích kiểm tra, các phần tử này có thể cố định trong trường dòng hoặc chuyển động cùng với đường dòng. Tuy nhiên, khác với thể tích kiểm tra, áp dụng các định luật vật lý, ta có thể trực tiếp tìm ra dạng vi phân của phương trình điều khiển. Dạng tích phân được tìm ra một cách gián tiếp bằng cách biến đổi từ dạng vi phân. Với trường hợp `1.c`, các phương trình này sẽ ở dạng **bảo toàn**. Với trường hợp `1.d`, các phương trình này ở dạng **không bảo toàn**.
{: .text-justify} 

---
Note:
  - `Control Volume` là gì? Trong cơ học liên tục và nhiệt động lực học, `Control Volume` là một khái niệm toán học dùng để diễn tả các mô hình vật lý bằng mô hình toán học. Hiểu theo cách đơn giản nhất, `Control Volume` là một khối thể tích hữu hạn của dòng chất lưu bất kỳ. Các định luật vật lý sẽ được áp dụng cho dòng chất lưu bên trong `Control Volume` và các dòng chất lưu chuyển động qua nó (nếu `Control Volume` cố định trong không gian).Do đó, thay vì tính toán trên cả trường, ta giới hạn mô hình trên `Control Volume`. Sau đó, áp dụng các phương pháp số với mô hình trên `Control Volume`, ta có thể tính toán kết qua cho toàn bộ dòng chất lưu.
  {: .text-justify}
  
  - Bề mặt bao kín thể tích kiểm tra `Control Volume` được gọi là `Control Surface`.
  {: .text-justify}

  - Trong trạng thái ổn định (*steady state*), thì khối lượng và động lượng của `Control Volume` được bảo toàn. Các bạn cũng có thể tham khảo thêm bài viết chi tiết hơn tại đây [tại đây](https://en.wikipedia.org/wiki/Control_volume).
  {: .text-justify}

---
#### Reference:
  1. Hirsch C. (2016). Numerical computation of internal and external flows. Volume 1.
  2. Anderson-J-D. (1996). Computational Fluid Dynamics: the Basics With Applications.