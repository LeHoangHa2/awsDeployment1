---
title : "Launch 50 instances"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre: <b> 6.1 </b>
---

### Objective:
Automatically deploy 50 EC2 instances using the optimized Custom AMI, with pre-configured User Data to verify scalability and configuration consistency.

### Deployment Method:
#### Option 1: Use AWS Launch Template + Auto Scaling Group
> Recommended for simplicity, efficiency, and easy scalability

##### Step 1: Create a Launch Template
- Navigate to **EC2 → Launch Templates → Create launch template**

- **Name**: `custom-ami-template`

- **AMI**: Select your optimized Custom AMI

- **Instance type**: `t2.micro`

- **Key Pair**: hoangha_keypair.pem

- **User Data**: Paste the script used in Chapter 5

- **Security Group**: Open port 22 and 80

  ![Template](/images/6.clean/create-template-1.png)
  ![Template](/images/6.clean/create-template-2.png)
  ![Template](/images/6.clean/create-template-3.png)


##### Step 2: Create an Auto Scaling Group
- **Go to EC2 → Auto Scaling → Create Auto Scaling group**
- Choose the **Launch Template** you just created
- Name: `asg-custom-50`
- Select subnet (multi-AZ or public subnet recommended)
- Set:
- **Desired capacity**: 50
- Min = Max = Desired = 50
- Disable scaling policies (no need for dynamic scaling)
- Click **Create**


![AutoScaling](/images/6.clean/autoscaling-1.png)
  ![AutoScaling](/images/6.clean/autoscaling-2.png)
  ![AutoScaling](/images/6.clean/autoscaling-3.png)
  ![AutoScaling](/images/6.clean/autoscaling-4.png)
  ![AutoScaling](/images/6.clean/autoscaling-5.png)
  ![AutoScaling](/images/6.clean/autoscaling-6.png)
  ![AutoScaling](/images/6.clean/autoscaling-7.png)
  ![AutoScaling](/images/6.clean/autoscaling-8.png)

  ### Verification:
- **Go to EC2 → Instances → Filter by Auto Scaling Group**

- Ensure all 50 instances:

- Are in "Running" state

- Serve the web interface (check port 80)
      ![AutoScaling](/images/6.clean/50instance.png)

### Conclusion:
- Using a Custom AMI and User Data allows you to quickly launch 50 fully configured EC2 instances in just a few minutes, eliminating the need for manual SSH setup, ensuring consistent configuration, and saving significant deployment time.