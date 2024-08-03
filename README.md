# Deploy-a-Static-Website-on-AWS-with-Docker
Instructions on how I deployed a Static Web App on AWS with Docker, Amazon ECR, and ECS services. 

## Infrastructure setup

**Create Dockerfile**

```bash
#!/bin/bash
sudo su
yum update -y
yum install -y httpd
cd /var/www/html
wget https://github.com/azeezsalu/jupiter/archive/refs/heads/main.zip
unzip main.zip
cp -r jupiter-main/* /var/www/html/
rm -rf jupiter-main main.zip
systemctl enable httpd 
systemctl start httpd
```
