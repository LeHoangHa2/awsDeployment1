---
title : "Apply user data to launch EC2."
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre: <b> 5.2 </b>
---

### Objective:
Integrate the User Data script written in Section 5.1 into the EC2 creation process so that the EC2 instance can automatically configure itself upon launch — without the need for manual SSH access.

### Steps to Follow:
- Reuse the simple script from Section 5.1.

### Create EC2 with User Data
1. Go to EC2 Console
2. Name: `ec2-test-user-data`
3. AMI: AWS Amazon Linux (or your custom AMI)
4. Instance type: t2.micro
5. Key Pair: Select hoangha_keypair.pem
6. Go to **Advanced details**
7. Paste your script into the **User data** section
8. Click **Launch Instance**

![EC2](/images/5/userdata-1.png)
![EC2](/images/5/userdata-2.png)
![EC2](/images/5/userdata-3.png)
![EC2](/images/5/userdata-4.png)
![EC2](/images/5/userdata-5.png)