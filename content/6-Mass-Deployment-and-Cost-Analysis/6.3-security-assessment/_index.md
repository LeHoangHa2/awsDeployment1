---
title : "Security Assessment"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre: <b> 6.3 </b>
---
### Objective
- Conduct performance benchmarking after deploying 50 EC2 instances from:
- **Custom AMI**: Pre-installed AWS CLI, CloudWatch Agent, unnecessary services disabled.
- **Standard AMI**: Default from AWS (Amazon Linux).
### Performance Metrics

| **Metric**                     | **Custom AMI** | **Standard AMI** |
| ------------------------------ | -------------- | ---------------- |
| ⏱ Average Boot Time            | \~28 seconds   | \~54 seconds     |
| 💾 RAM Usage after Boot        | \~130MB        | \~300MB          |
| 📋 CloudWatch Log Preinstalled | ✅ Yes          | ❌ No             |
| ⚙️ Consistent Configuration    | ✅ Yes          | ❌ No             |
| 🚀 Time to Deploy 50 EC2s      | \~3 minutes    | \~10 minutes     |

### Measurement Methods

- `uptime -s`: Measure boot time after startup.

- `free -m`: Check RAM usage immediately after boot.

- **CloudWatch Metrics**: Monitor CPU idle, memory available.

- SSH into 5 random instances: check CloudWatch Agent, logging, and user-data setup.

- Compare logs in Launch Template / Auto Scaling: evaluate deployment speed.

![AutoScaling](/images/6.clean/50instance.png)
  ![AutoScaling](/images/6.clean/hieunang5conEC2.png)

 ### Observation
- Using a Custom AMI reduces boot time by 50%, saves memory, and enables automatic logging immediately after EC2 startup.
- Standard AMIs require additional time for software installation and configuration.
- Custom AMIs are optimal for rapid deployment in Production, CI/CD, or Auto Scaling environments.
### Conclusion:
This benchmark demonstrates that Custom AMIs simplify and optimize the process of mass-deploying EC2 instances on AWS. Combined with User Data, it ensures all instances are fully ready right after boot.