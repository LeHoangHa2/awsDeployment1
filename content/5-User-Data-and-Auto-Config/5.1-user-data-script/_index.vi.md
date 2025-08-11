---
title : "Tạo mẫu User data"
slug: "user-data-script"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre: <b> 5.1 </b>
---

### Mục tiêu:
Viết một bash script để EC2 tự động thực hiện các tác vụ cấu hình ban đầu ngay sau khi khởi tạo, giúp tiết kiệm thời gian triển khai.

---

### Ý tưởng nội dung script:

- Cập nhật hệ thống
- Cài đặt nginx (web server)
- Ghi log boot vào file
- Tự động khởi động dịch vụ

---

### Mẫu script đơn giản :

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
### Mẫu Script phức tạp: 
```bash
#!/bin/bash
# Cập nhật toàn bộ hệ thống
yum update -y

# Cài Apache Web Server
yum install -y httpd
systemctl start httpd
systemctl enable httpd

# Nếu cần chào mừng đơn giản
echo "<h1>Welcome from $(hostname -f)</h1>" > /var/www/html/index.html

# Cài Amazon CloudWatch Agent
yum install -y amazon-cloudwatch-agent

# Tạo file cấu hình mẫu cho CloudWatch Agent
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

# Khởi động agent với cấu hình đã tạo
/opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl \
  -a fetch-config \
  -m ec2 \
  -c file:/opt/aws/amazon-cloudwatch-agent/etc/amazon-cloudwatch-agent.json \
  -s

# Mở port 80 nếu cần (chỉ cần nếu đang dùng firewalld, còn không thì nên bỏ qua)
/usr/bin/which firewall-cmd && firewall-cmd --permanent --add-port=80/tcp && firewall-cmd --reload || echo "firewalld not installed, skip opening port"

echo "DONE INIT SCRIPT"

```
