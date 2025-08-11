---
title : "Tạo EC2 từ AMIs"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 3.1 </b> "
---

Việc khởi tạo này rất quan trọng trong quy trình đánh giá hiệu năng, vì chúng ta sẽ tiếp tục đo thời gian boot, độ ổn định, và so sánh với EC2 tạo từ AMI chuẩn (standard AMI) của AWS

1. Đi tới [AMIs](https://ap-southeast-1.console.aws.amazon.com/ec2/home?region=ap-southeast-1#Images:visibility=owned-by-me)
  + Nhấn vào **Launch instance from AMI**.

  ![Create EC2](/images/3.s3/createec2-fromami-0.png)

  + Tên : `Custom-EC2-from-AMI`.
  + Nhấp chọn **Keypair**.
  + Nhấp chọn **Network**.
  + Cuối cùng chọn **Launch instance**.

  ![Create EC2](/images/3.s3/abc.png)

  ![Create EC2](/images/3.s3/createec2-fromami-2.png)

  ![Create EC2](/images/3.s3/createec2-fromami-3.png)
