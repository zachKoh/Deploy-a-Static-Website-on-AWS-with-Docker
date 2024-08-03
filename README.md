# Deploy-a-Static-Website-on-AWS-with-Docker
Instructions on how I deployed a Static Web App on AWS with Docker, Amazon ECR, and ECS services.

## Infrastructure setup

**Created Dockerfile**
- Created the dockerfile using this script
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

**Building/pushing the docker image**
- Built the container image
- Started the container image
- Pushed the image to the Docker hub repository
- Logged into AWS CLI using an IAM user with adminstrator access
- Created ECR repository to store the image
- Pushed the docker image to the ECR repository

**Building the AWS infrastructure**
- Built VPC with 2 public subnets and 4 private subnets
- Created 2 NAT gateways in the two public subnets in different availability zones
- Create security groups and application load balancer
- Created ECS cluster, task definition, and service
- Registered domain and create an A record to host the website through my ALB
