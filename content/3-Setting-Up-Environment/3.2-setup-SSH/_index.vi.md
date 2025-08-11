---
title : "Kết nối SSH"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 3.2 </b> "
---
Chúng ta đã khởi tạo EC2 từ AMIs thành công, Và giờ đây chúng ta sẽ thử kết nối qua SSH để xem có hoạt động được hay không?


1. Đi tới [EC2](https://ap-southeast-1.console.aws.amazon.com/ec2/home?region=ap-southeast-1#Instances:v=3;$case=tags:true%5C,client:false;$regex=tags:false%5C,client:false;sort=tag:Name)
   + Nhấp **connect**.
   + Nhâp **SSH Client**
   + Sau đó copy 
   
   ![EC2](/images/3.s3/connectec2-1.png)
   ![EC2](/images/3.s3/connectec2-2.png)
   ```bash
   ssh -i "hoangha_keypair.pem" root@ec2-13-213-39-234.ap-southeast-1.compute.amazonaws.com
   ```
   Do tạo từ AMIs nên sẽ bị lỗi root, các bạn hãy đổi **root** thành **ec2-user** để có thể connect được nha.
   ![EC2](/images/3.s3/connect-ssh-0.png)
   ![EC2](/images/3.s3/connect-ssh-1.png)


