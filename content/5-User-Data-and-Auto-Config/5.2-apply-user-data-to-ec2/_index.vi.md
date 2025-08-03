---
title : "Áp dụng userdata để tạo EC2"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre: <b> 5.2 </b>
---

### Mục tiêu:
Tích hợp script User Data đã viết ở phần **5.1** vào quá trình tạo EC2, để EC2 có thể tự động cấu hình ngay khi được khởi tạo – không cần SSH thủ công.

---

### 🛠 Các bước thực hiện:
- Dùng lại script đơn giản từ phần **5.1**.

### Tạo EC2 với User Data
1. Truy cập [EC2](https://ap-southeast-1.console.aws.amazon.com/ec2/home?region=ap-southeast-1#Instances:v=3;$case=tags:true%5C,client:false;$regex=tags:false%5C,client:false;sort=tag:Name)

2. Tên : `ec2-test-user-data`

3. AMI: AWS Amazon Linux (hoặc Custom AMI bạn đã tạo)

4. Instance type: t2.micro

5. Key Pair: Chọn hoangha_keypair.pem

6. **Advanced details**

7. Thả Script vào **User data**

8. Nhấn **Launch Instance**

![EC2](/images/5/userdata-1.png)
![EC2](/images/5/userdata-2.png)
![EC2](/images/5/userdata-3.png)
![EC2](/images/5/userdata-4.png)
![EC2](/images/5/userdata-5.png)
