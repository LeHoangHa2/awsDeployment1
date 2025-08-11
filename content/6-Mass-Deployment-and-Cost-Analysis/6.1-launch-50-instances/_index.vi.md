---
title : "Triển khai hàng loạt 50 EC2 từ Custom AMI"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre: <b> 6.1 </b>
---

### Mục tiêu:
Tự động triển khai 50 EC2 instances từ Custom AMI đã tối ưu, áp dụng sẵn User Data để kiểm chứng khả năng mở rộng và tính đồng nhất trong cấu hình.

---

###  Cách triển khai:

####  Cách 1: Dùng **AWS Launch Template + Auto Scaling Group**

> Khuyên dùng vì đơn giản, hiệu quả và có thể scale theo số lượng mong muốn

##### Bước 1: Tạo Launch Template

- Vào **EC2 → Launch Templates → Create launch template**
- **Tên**: `custom-ami-template`
- **AMI**: Chọn AMI bạn đã tạo (Custom AMI)
- **Instance type**: `t2.micro`
- **Key Pair**: `hoangha_keypair.pem`
- **User Data**: Dán script đã dùng ở chương 5
- **Security Group**: Mở port 22 và 80
  ![Template](/images/6.clean/create-template-1.png)
  ![Template](/images/6.clean/create-template-2.png)
  ![Template](/images/6.clean/create-template-3.png)

##### Bước 2: Tạo Auto Scaling Group

- **EC2 → Auto Scaling → Create Auto Scaling group**
- Chọn **Launch Template** bạn vừa tạo
- Đặt tên: `asg-custom-50`
- Chọn subnet (multi-AZ hoặc public subnet)
- **Desired capacity**: `50`
- Min = Max = Desired = `50`
- Tắt scaling policy (không cần dynamic scale)
- Nhấn **Create**
  ![AutoScaling](/images/6.clean/autoscaling-1.png)
  ![AutoScaling](/images/6.clean/autoscaling-2.png)
  ![AutoScaling](/images/6.clean/autoscaling-3.png)
  ![AutoScaling](/images/6.clean/autoscaling-4.png)
  ![AutoScaling](/images/6.clean/autoscaling-5.png)
  ![AutoScaling](/images/6.clean/autoscaling-6.png)
  ![AutoScaling](/images/6.clean/autoscaling-7.png)
  ![AutoScaling](/images/6.clean/autoscaling-8.png)
  


---

### 🔍 Kiểm tra:

- Vào EC2 → Instances → filter theo Auto Scaling Group
- Kiểm tra 50 máy có:
  - Chạy trạng thái “Running”
  - Giao diện web hoạt động (port 80)
  ![AutoScaling](/images/6.clean/50instance.png)
  

---

### Kết luận:

Custom AMI + User Data giúp tạo nhanh 50 EC2 hoàn chỉnh chỉ trong vài phút, không cần SSH từng máy, đảm bảo cấu hình đồng nhất và tiết kiệm thời gian triển khai.


