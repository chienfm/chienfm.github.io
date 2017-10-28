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

Khi xem xét một khối rắn trong chuyển động tịnh tiến, chúng ta thấy rằng vận tốc của mọi phần của khối này là như nhau. Tuy nhiên, đối với chuyển động của khối chất lưu, vận tốc của mỗi phần trong khối này có thể không giống nhau. Vậy làm cách chúng ta có thể quan sát một khối chất lưu chuyển động rồi từ đó có thể áp dụng các định luật vật lý? Trong môi trường chất lưu liên tục, chúng ta có thể giải quyết vấn đề đó bằng cách áp dụng 1 trong 4 mô hình sau
{: .text-justify}

### 1.1 Khối thể tích hữu hạn (Finite Control Volume)

<center>
<figure>
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/filename.jpg" alt="Mô hình hóa dòng chảy" width="370" height="300">
  <figcaption>Hình 1. Mô hình hóa dòng chất lưu.</figcaption>
</figure>
</center>


### 1.2 Phần tử thể tích hữu hạn (Infinitesimal Fluid Element)


---
Note:
  - `Control Volume` là gì? Trong cơ học liên tục và động lực học, `Control Volume` là 1 khái niệm toán học dùng để diễn tả các mô hình vật lý bằng mô hình toán học. Hiểu 1 cách đơn giản nhất, `Control Volume` là một khối nhỏ của 1 hệ mà mọi định luật vật lý áp dụng lên hệ đều có thể áp dụng lên khối này. Bề mặt bao kín `Control Volume` được gọi là `Control Surface`. Trong trạng thái ổn định (*steady state*), thì khối lượng và động lượng của `Control Volume` được bảo toàn. Các bạn cũng có thể tham khảo thêm [tại đây](https://en.wikipedia.org/wiki/Control_volume)
  {: .text-justify}