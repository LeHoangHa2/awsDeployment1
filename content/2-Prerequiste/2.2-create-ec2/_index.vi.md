---
title : "Tạo EC2"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---
### Tạo EC2


Trong bước này, chúng tôi triển khai một EC2 instance từ AMI gốc (Amazon Linux 2), sử dụng loại máy t2.micro (1 vCPU, 1GB RAM). Mục tiêu là xây dựng một môi trường tiêu chuẩn để tối ưu hóa, đóng gói thành Custom AMI, giúp tăng tốc thời gian khởi động và triển khai ứng dụng nhanh chóng sau này.

1. Truy cập [EC2](https://ap-southeast-1.console.aws.amazon.com/ec2/home?region=ap-southeast-1#Instances:v=3;$case=tags:true%5C,client:false;$regex=tags:false%5C,client:false)
   + Tìm kiếm **EC2**.
   + Nhấp vào **EC2**, sau dó Nhấp vào **Launch instance** to confirm.

![role](/images/2.prerequisite/Createec2_1.png)

![role1](/images/2.prerequisite/Createec2-2.png)

2. Truy cập [Create function](https://ap-southeast-1.console.aws.amazon.com/ec2/home?region=ap-southeast-1#LaunchInstances:)
  + Tên: `EC2-Server`
  + Nhấp vào **AWS: Amazon Linux**
  + Nhấp vào **Tạo Key pair**
  + Nhấp vào **VPC Created**
  + Nhấp vào public subnet
  + Nhấp vào Security Group
  + Nhấp vào **IAM instance profile**
  + Nhấp vào **check information configure storage and Launch  Instance**
![role1](/images/2.prerequisite/Createec2_3-1.png)
![role2](/images/2.prerequisite/Createec2_3.png)

![createpolicy](/images/2.prerequisite/Createec2_4.png)

![namerole](/images/2.prerequisite/Createec2_5.png)


![namerole1](/images/2.prerequisite/Createec2_6.png)


### Nội dung
  - [Create AMI](../2.3-create-AMI/)