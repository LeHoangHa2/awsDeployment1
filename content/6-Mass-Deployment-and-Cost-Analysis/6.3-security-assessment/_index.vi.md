---
title : "Benchmark"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre: <b> 6.3 </b>
---


🌟 Mục tiêu

- Tiến hành đo độ hiệu năng sau khi triển khai 50 EC2 instance từ:

- Custom AMI: Đã cài sẵn AWS CLI, CloudWatch Agent, tinh chỉnh bỏ dịch vụ không cần thiết

- Standard AMI: Mặc định từ AWS (Amazon Linux)
## 🔬 Chỉ số đo hiệu năng

| **Chỉ số**                  | **Custom AMI**     | **Standard AMI**   |
|----------------------------|--------------------|--------------------|
| ⏱ Boot time trung bình     | ~28 giây           | ~54 giây           |
| 💾 RAM sau khi khởi động    | ~130MB             | ~300MB             |
| 📋 Cài sẵn CloudWatch Log   | ✅ Có              | ❌ Không           |
| ⚙️ Cấu hình đồng nhất       | ✅ Có              | ❌ Không           |
| 🚀 Thời gian deploy 50 EC2 | ~3 phút            | ~10 phút           |


⚙️ Phương pháp đo

- `uptime -s`: Đo thời gian boot sau khi khởi động xong

- `free -m`: Kiểm tra bộ nhớ RAM dùng khi mới boot

- **CloudWatch Metrics**: CPU idle, memory available

- SSH ngẫu nhiên 5 instance: check cài đặt CloudWatch Agent, logging, user-data

- So sánh log ở Launch Template / Auto Scaling: tốc độ deploy

<!-- 📸 Hình ảnh minh chứng

img/6.4-instance-list.png: Danh sách 50 instance

img/6.4-uptime-check.png: 5 uptime ngẫu nhiên


img/6.4-free-mem-check.png: RAM sau boot

img/6.4-cloudwatch-active.png: Agent đang hoạt động

img/6.4-auto-scaling-speed.png: Log triển khai -->
![AutoScaling](/images/6.clean/50instance.png)
  ![AutoScaling](/images/6.clean/hieunang5conEC2.png)




### Nhận xét

- Việc sử dụng Custom AMI giúp giảm 50% thời gian khởi động, tiết kiệm RAM, và tự động logging ngay khi EC2 boot xong

- Standard AMI mất nhiều thời gian do phải cài lại phần mềm và cấu hình lại

- Custom AMI là giải pháp tối ưu để triển khai nhanh trong môi trường Production, CI/CD, hoặc autoscaling

### Kết luận: 
- Việc benchmark chứng minh Custom AMI giúp đơn giản hoá và tối ưu hoá quy trình triển khai hàng loạt instance trên AWS. Việc tích hợp User Data giúp toàn bộ máy đạt trạng thái sẵn sàng nhanh nhất sau khi boot.