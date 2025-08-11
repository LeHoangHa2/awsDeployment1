---
title : "Create AMI"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 2.3 </b> "
---

### Create AMI
After successfully launching an EC2 instance named Custom-ami-base-server, we proceed to install the following:

AWS CLI to enable interaction with AWS services

CloudWatch Agent to monitor system resources (CPU, RAM, disk, network, etc.)

System optimizations such as disabling unnecessary services, reducing boot time, and applying basic security configurations

1. Truy cập [EC2](https://ap-southeast-1.console.aws.amazon.com/ec2/home?region=ap-southeast-1#Instances:v=3;$case=tags:true%5C,client:false;$regex=tags:false%5C,client:false)
    + Name: `Custom-ami-base-server` .
    + Click **Action**, Click **Image and Templates**.
    + Click **Create Image**.

  ![AMI](/images/2.prerequisite/Createiam-1.png)

2. Truy cập [Create Function](https://ap-southeast-1.console.aws.amazon.com/ec2/home?region=ap-southeast-1#CreateImage:instanceId=i-0ed4a1e16f974567a)

    + Name: `Custom-ami-ec2-optimized` /**Name: Custom-ami-ec2-optimized**.
    
    ![AMI](/images/2.prerequisite/Createiam-2.png)

    + Check status AMIs

    ![AMI](/images/2.prerequisite/Createiam-3.png)