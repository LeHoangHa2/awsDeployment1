---
title : "Connect SSH"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 3.2 </b> "
---
We have successfully launched an EC2 instance from the AMIs, and now we will try connecting via SSH to verify if it is working properly.

1. Đi tới [EC2](https://ap-southeast-1.console.aws.amazon.com/ec2/home?region=ap-southeast-1#Instances:v=3;$case=tags:true%5C,client:false;$regex=tags:false%5C,client:false;sort=tag:Name)
   + Click **connect**.
   + Click **SSH Client**
   + Copy 
   ```bash
   ssh -i "hoangha_keypair.pem" root@ec2-18-136-195-220.ap-southeast-1.compute.amazonaws.com
   ```
   ![EC2](/images/3.s3/connectec2-1.png)
   ![EC2](/images/3.s3/connectec2-2.png)
   ![EC2](/images/3.s3/connectec2-3.png)