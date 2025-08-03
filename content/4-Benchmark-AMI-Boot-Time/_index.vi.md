---
title : "Đo hiệu suất thời gian khởi động của AMI"
date :  "`r Sys.Date()`" 
weight : 4 
chapter : false
pre : " <b> 4. </b> "
---

Trong bước này chúng ta sẽ tối ưu hóa hiệu suất khởi động của **AMI (Amazon Machine Image)**, việc thiết lập sẵn môi trường dịch vụ trước khi tạo AMI là một bước quan trọng nhằm giảm thời gian cấu hình sau khi EC2 được khởi chạy. Trong bước này, chúng tôi tiến hành thiết lập **Custom AMI** và **Standard AMI**

+ Đo thời gian boot thực tế

### Nội dung:
   - [Tạo **Custom AMI**](./4.1-custom-ami-benchmark/)
   - [Tạo **Standard AMI**](./4.2-standard-ami-benchmark/)
