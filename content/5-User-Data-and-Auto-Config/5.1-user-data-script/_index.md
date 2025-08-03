---
title : "Create User data"
slug: "user-data-script"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre: <b> 5.1 </b>
---

### Objective:

Write a Bash script to automatically perform initial configuration tasks on an EC2 instance immediately after launch, saving deployment time.

### Script Concept:
- System update
- Install nginx or Apache (web server)
- Log boot metadata
- Automatically start services

### Simple Script Example:

```bash
#!/bin/bash
yum install httpd -y
service httpd start
systemctl enable httpd

cd /var/www/html
echo "<html>" > index.html

echo "<h1>Welcome to MyWebsite</h1>" >> index.html
echo "<h3>You are running instance from this IP:</h3>" >> index.html

echo "<br>Private IP: " >> index.html
curl http://169.254.169.254/latest/meta-data/local-ipv4 >> index.html

echo "<br>Public IP: " >> index.html
curl http://169.254.169.254/latest/meta-data/public-ipv4 >> index.html 

echo "</html>" >> index.html
```

### Advanced Script Example:
```bash
#!/bin/bash
# Update the entire system
yum update -y

# Install Apache Web Server
yum install -y httpd
systemctl start httpd
systemctl enable httpd

# Simple welcome message
echo "<h1>Welcome from $(hostname -f)</h1>" > /var/www/html/index.html

# Install Amazon CloudWatch Agent
yum install -y amazon-cloudwatch-agent

# Create default config file for CloudWatch Agent
cat <<EOF > /opt/aws/amazon-cloudwatch-agent/etc/amazon-cloudwatch-agent.json
{
  "metrics": {
    "append_dimensions": {
      "InstanceId": "\${aws:InstanceId}",
      "InstanceType": "\${aws:InstanceType}"
    },
    "metrics_collected": {
      "cpu": {
        "measurement": [
          "cpu_usage_idle",
          "cpu_usage_iowait",
          "cpu_usage_user",
          "cpu_usage_system"
        ],
        "metrics_collection_interval": 60
      },
      "mem": {
        "measurement": [
          "mem_used_percent"
        ],
        "metrics_collection_interval": 60
      }
    }
  }
}
EOF

# Start CloudWatch Agent with config
/opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl \
  -a fetch-config \
  -m ec2 \
  -c file:/opt/aws/amazon-cloudwatch-agent/etc/amazon-cloudwatch-agent.json \
  -s

# Open port 80 (optional – skip if firewalld is not used)
/usr/bin/which firewall-cmd && firewall-cmd --permanent --add-port=80/tcp && firewall-cmd --reload || echo "firewalld not installed, skipping port opening"

echo "DONE INIT SCRIPT"
```