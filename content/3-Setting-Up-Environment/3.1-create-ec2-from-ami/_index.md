---
title : "Create EC2 from AMIs"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 3.1. </b> "
---

This initialization is a crucial step in the performance evaluation process, as we will continue to measure boot time, system stability, and compare it with EC2 instances launched from AWS standard AMIs.

1. Go [AMIs](https://ap-southeast-1.console.aws.amazon.com/ec2/home?region=ap-southeast-1#Images:visibility=owned-by-me)
  + Click **Launch instance from AMI**.

  ![Create EC2](/images/3.s3/createec2-fromami-0.png)

  + Name : `test-from-custom-ami`.
  + Click **Keypair**.
  + Click **Network**.
  + Click **Launch instance**.

  ![Create EC2](/images/3.s3/createec2-fromami-1.png)

  ![Create EC2](/images/3.s3/createec2-fromami-2.png)

  ![Create EC2](/images/3.s3/createec2-fromami-3.png)

  