---
layout: single
title:  "CFD - Phương trình cơ bản 1"
header:
  teaser: "unsplash-gallery-image-2-th.jpg"
categories: 
  - Jekyll
tags:
  - edge case
---
Các biến của phương pháp cơ học tính toán, dù ở dạng nào, đều được dựa trên các tính chất cơ bản của cơ học chất lỏng bao gồm `tính liên tục (continuity)`, `động lượng (momentum)` và `năng lượng (energy)`. Chúng được khái quát hóa bằng các định luật toán học cơ bản sau:
  - Định luật bảo toàn khối lượng.
  - Định luật 2 Newton $F = ma$.
  - Định luật bảo toàn năng lượng.

Trong chương này, chúng ta sẽ cùng thực hiện các biến đổi để xây dựng ra các phương trình đặc trưng cũng như sẽ cùng thảo luận để hiểu kĩ hơn về tính chất và ý nghĩa của chúng. Hiểu rõ cách xây dựng và ý nghĩa của phương trình giúp bạn nắm rõ cách vận dụng và có thể tự phát triển các công cụ tính toán sau này. Do nội dung