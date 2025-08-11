---
  title : "Thiết lập Standard-AMI"
  date : "`r Sys.Date()`"
  weight : 2
  chapter : false
  pre : " <b> 4.2 </b> "
---


## 4.2 - Benchmark Standard AMI Boot Time

### 🎯 Mục tiêu:
Đo thời gian khởi động (boot time) của một EC2 instance sử dụng **Standard AMI của AWS** (ví dụ: Ubuntu Server hoặc Amazon Linux), để so sánh với Custom AMI đã tối ưu ở bước trước.

---

### 🛠 Các bước thực hiện:

#### Tạo EC2 từ Standard AMI

1. Truy cập [EC2](chttps://ap-southeast-1.console.aws.amazon.com/ec2/home?region=ap-southeast-1#Instances:v=3;$case=tags:true%5C,client:false;$regex=tags:false%5C,client:false;sort=tag:Name)
 - Chọn **Launch Instance**
2. **Tên**: `Standard-AMI`
3. **AMI**: Amazon Linux 2023
4. **Instance type**: `t2.micro`
5. **Key Pair**: Sử dụng `hoangha_keypair.pem`
6. **Network**: Chọn VPC và Public Subnet, bật Auto-assign Public IP
7. **Security Group**: Mở port 22 (SSH)
8. Nhấn **Launch Instance**
9. Ghi lại thời điểm bạn nhấn Launch (ví dụ: `07:31:00`)

![EC2](/images/4/standardami-1.png) 
![EC2](/images/4/standardami-2.png) 
---

#### Chạy SSH vào instance và đo boot time

1. Dùng đúng user (tùy AMI):
   - Ubuntu AMI:  
     ```bash
     ssh -i "hoangha_keypair.pem" ubuntu@<public-ip>
     ```
   - Amazon Linux:  
     ```bash
     ssh -i "hoangha_keypair.pem" ec2-user@<public-ip>
     ```

2. Sau khi đăng nhập thành công, chạy:
  ```bash
   uptime -s
  ```
![Standard](/images/4/standardami-3.png) 