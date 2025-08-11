---
title : "Tạo AMI"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 2.3 </b> "
---
### Tạo AMI
Sau khi triển khai thành công một EC2 instance với tên **Custom-ami-base-server**, ta tiến hành cài đặt thêm:

   - AWS CLI để hỗ trợ tương tác với các dịch vụ AWS

   - CloudWatch Agent để giám sát tài nguyên hệ thống (CPU, RAM, disk, network…)

   - Các tinh chỉnh hệ thống như tắt dịch vụ không cần thiết, tối ưu thời gian boot, và cấu hình bảo mật cơ bản

1. Truy cập [EC2](https://ap-southeast-1.console.aws.amazon.com/ec2/home?region=ap-southeast-1#Instances:v=3;$case=tags:true%5C,client:false;$regex=tags:false%5C,client:false)
    + Tên: **EC2_Server** .
    + Nhấp **Action**, sau đó nhấp **Image and Templates**.
    + Nhấp chọn **Create Image**.
  ![AMI](/images/2.prerequisite/Createami-10.png)
2. Truy cập [Create Function](https://ap-southeast-1.console.aws.amazon.com/ec2/home?region=ap-southeast-1#CreateImage:instanceId=i-0ed4a1e16f974567a)

    + Tên: `Custom-ami-ec2-optimized` /**Name: Custom-ami-ec2-optimized**.
    
    ![AMI](/images/2.prerequisite/Createiam-2-1.png)

    + Kiểm tra tình trạng AMIs

    ![AMI](/images/2.prerequisite/Createiam-3.png)