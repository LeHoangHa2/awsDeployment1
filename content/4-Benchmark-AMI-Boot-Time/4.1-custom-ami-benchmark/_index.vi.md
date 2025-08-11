---
  title : "Thiết lập Custom-AMI"
  date : "`r Sys.Date()`"
  weight : 1
  chapter : false
  pre : " <b> 4.1 </b> "
---


## 4.1 - Benchmark Custom AMI Boot Time

### 🎯 Mục tiêu:
Đo thời gian khởi động (boot time) thực tế của một EC2 instance được khởi tạo từ **Custom AMI** đã tối ưu hóa trước đó.

---

### 🛠 Các bước thực hiện:

1. Truy cập [AMIs](https://ap-southeast-1.console.aws.amazon.com/ec2/home?region=ap-southeast-1#Images:visibility=owned-by-me)
2. Chọn Custom AMI đã tạo từ instance cấu hình sẵn
3. Nhấn **Launch instance from image**
4. Thiết lập thông tin:
   - Tên: `Custom_AMI` 
   - Loại máy: `t2.micro`
   - Key Pair: `hoangha_keypair`
   - VPC/Subnet: public subnet, auto-assign public IP
   - Security Group: mở port 22
5. Nhấn **Launch Instance**
6. Ghi lại thời điểm nhấn Launch

![AMIs](/images/4/customami-1.png)
![AMIs](/images/4/customami-2.png)
![AMIs](/images/4/customami-3.png)

---

### 🔐 Kết nối & đo thời gian boot:

1. SSH vào EC2:
```bash
ssh -i "hoangha_keypair.pem" ec2-user@ec2-54-255-53-31.ap-southeast-1.compute.amazonaws.com
```
2. Chạy lệnh 
```bash 
uptime -s
```
![SSH](/images/4/customami-4.png)

Mất 8s 

