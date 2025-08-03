---
title : "Create ec2"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---

### Create EC2

In this step, we will launch an EC2 instance from the base AMI (Amazon Linux 2), using a t2.micro instance type (1 vCPU, 1GB RAM). The goal is to build a standard environment for optimization, which will later be packaged into a Custom AMI to accelerate boot time and enable faster application deployment.

1. Go to [EC2](https://ap-southeast-1.console.aws.amazon.com/ec2/home?region=ap-southeast-1#Instances:v=3;$case=tags:true%5C,client:false;$regex=tags:false%5C,client:false)
   + Search **EC2**.
   + Click **EC2**, then click **Launch instance** to confirm.

![role](/images/2.prerequisite/Createec2_1.png)

![role1](/images/2.prerequisite/Createec2-2.png)

1. Go to [Create function](https://ap-southeast-1.console.aws.amazon.com/ec2/home?region=ap-southeast-1#LaunchInstances:)
+ Name: `EC2-Server`
+ Click AWS: **Amazon Linux**
+ Click **Create Key pair**
+ Click **VPC** Created
+ Click public subnet
+ Click Security Group
+ Click **IAM instance profile**
+ Click **check information configure storage and Launch Instance**
![role1](/images/2.prerequisite/Createec2_3-1.png)
![role2](/images/2.prerequisite/Createec2_3.png)

![createpolicy](/images/2.prerequisite/Createec2_4.png)

![namerole](/images/2.prerequisite/Createec2_5.png)


![namerole1](/images/2.prerequisite/Createec2_6.png)
### Content
  - [Create AMI](../2.3-create-AMI/)