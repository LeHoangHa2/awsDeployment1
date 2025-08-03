---
title : "Cost Analysis"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre: <b> 6.2 </b>
---

### Objective:
- Estimate the cost of deploying 50 EC2 instances using a pre-optimized Custom AMI, compare it with the traditional method using Standard AMI, and evaluate the cost-effectiveness of using Custom AMI + User Data.
### 1. Deployed System Specifications

| Parameter         | Value                            |
| ----------------- | -------------------------------- |
| Number of EC2s    | 50 instances                     |
| Instance type     | `t2.micro`                       |
| AMI used          | Custom AMI (pre-installed setup) |
| Deployment region | ap-southeast-1 (Singapore)       |
| Runtime duration  | 1 hour (example for comparison)  |

### 2. Estimated Cost (based on July 2025 pricing)
#### Reference price for `t2.micro` in ap-southeast-1:
- $0.0128 USD/hour (**on-demand** pricing, excluding taxes)

| Item                   | Value                   |
| ---------------------- | ----------------------- |
| Cost per EC2/hour      | \$0.0128                |
| Cost for 50 EC2s/hour  | \$0.0128 × 50 = \$0.64  |
| Cost for 50 EC2s/day   | \$0.64 × 24 = \$15.36   |
| Cost for 50 EC2s/month | \$15.36 × 30 = \$460.80 |
>🔸 Note: prices may vary by region and billing tier.
### 3. Cost Comparison: Custom AMI vs. Standard AMI
| Criteria                | Custom AMI                    | Standard AMI                        |
| ----------------------- | ----------------------------- | ----------------------------------- |
| Boot time               | Faster (30–40s)               | Slower (50–60s)                     |
| Pre-installed software  | Yes (nginx, logs, etc.)       | No                                  |
| Reinstallation effort   | None                          | Required (takes minutes per server) |
| Operating cost          | Same (same instance type)     | Same                                |
| **Total indirect cost** | **Lower due to time savings** | Higher due to manual setup          |
### 4. Overall Remarks
- In terms of **EC2 instance cost**, using either AMI results in the same charge if the instance type is the same.
- However, **Custom AMI saves significant deployment time**, especially when deploying 50–100+ servers.
- Combined with User Data scripts, it enables:
- Fully automated deployment without SSH
- Reduced manual error
- Lower operational labor cost

### Conclusion:
- While the EC2 price remains unchanged, using Custom AMI + User Data eliminates **hidden** costs like:
-nDevOps engineer time
- Misconfiguration risks
- Inconsistent server setup
→ This approach is a **cost-effective, standardized, and scalable solution** when expanding systems on AWS.