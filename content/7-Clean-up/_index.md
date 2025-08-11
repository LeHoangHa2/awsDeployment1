---
title : "Cleanup"
date :  "`r Sys.Date()`" 
weight : 7 
chapter : false
pre : " <b> 7. </b> "
---

### Objective
- Delete all unused resources to avoid incurring unnecessary AWS costs.

- reserve any data/system snapshots for reporting or future reuse.

- Ensure safety: avoid accidentally deleting important resources in your AWS account.

#### Cleanup Steps
Step 1: Stop & delete **Auto Scaling Groups**  
![Clean](/images/7.Cleanup/delete-1.png)  

Step 2: Delete **AMIs**.  
![Clean](/images/7.Cleanup/delete-2.png)  

Step 3: Delete **Launch Template**.  
![Clean](/images/7.Cleanup/delete-3.png)  

Step 4: Go to **EC2** and check the status of the 50 instances. Wait 2–3 minutes for the instances to show **Terminated** status, indicating successful deletion.  
![Clean](/images/7.Cleanup/delete-4-1.png)  
![Clean](/images/7.Cleanup/delete-4.png)  
