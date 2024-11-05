---
title : "Cài đặt EC2 instances"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 4.1 </b> "
---

# Tạo ec2 instance
* Name: ```ec2-streamlit-1d```.
* Chọn AMI: **Amazon Linux 2023 AMI**.
* Chọn instance type: **t2.micro**.
![ec21](/workshop-aws-card-clash-1/images/4.s3/ec21.png)
* Chọn key pair nếu muốn.
* Chọn default VPC nếu muốn setup đơn giản hoặc có thể dùng custom VPC bạn đã tạo.
* Chọn subnet trong AZ: us-east-1d.
* Security Group inbound rules:
    * Do streamlit application chạy port 8080, ta mở port 8080 và source 0.0.0.0/0.
    * Do cần connect với MySQL, ta mở port 3306 và source 0.0.0.0/0.
    * Do cần ssh vào ec2 instance, ta mở port 22 và source 0.0.0.0/0.
![ec22](/workshop-aws-card-clash-1/images/4.s3/ec22.png)
* Ở Advanced details, tại mục IAM instance profile: chọn role mình đã tạo ở bước chuẩn bị.
![ec23](/workshop-aws-card-clash-1/images/4.s3/ec23.png)
* Chọn **Launch instance**.
