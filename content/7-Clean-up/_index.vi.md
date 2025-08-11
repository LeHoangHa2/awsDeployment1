---
title : "Dọn dẹp tài nguyên"
date :  "`r Sys.Date()`" 
weight : 7 
chapter : false
pre : " <b> 7. </b> "
---

### Mục tiêu
- Xóa toàn bộ tài nguyên không còn sử dụng để tránh phát sinh chi phí AWS không cần thiết.

- Giữ lại các dữ liệu/ảnh chụp hệ thống phục vụ báo cáo hoặc tái sử dụng.

- Đảm bảo an toàn: không xóa nhầm tài nguyên quan trọng của tài khoản AWS.

#### Các bước dọn dẹp
Bước 1: Dừng & xóa **Auto Scaling Groups**
![Clean](/images/7.Cleanup/delete-1.png)
Bước 2: Xóa **AMIs**.
![Clean](/images/7.Cleanup/delete-2.png)
Bước 3: Xóa **Launch Temple**.
![Clean](/images/7.Cleanup/delete-3.png)
Bước 4: Vào **EC2** kiểm tra trạng thái 50 instance, Đợi 2-3p đợi instance hiển thị **Terminated** là xóa thành công
![Clean](/images/7.Cleanup/delete-4-1.png)
![Clean](/images/7.Cleanup/delete-4.png)





