---
title : "Tạo Application Load Balancer"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 5.2 </b> "
---
* Vào mục **Load Balancers**:
* Chọn **Create Load balancer**.
* Chọn **Application Load Balancer**.
![architecture-serverless](/workshop-aws-card-clash-1/images/5.fwd/lb1.png)
* Name: ```chatbot-alb```
* Chọn Scheme: internet-facing.
* Chọn IP address type: IPv4.
* Chọn VPC default.
* Các AZ: chọn 2 AZs us-east-1a và us-east-1d.
* Security group bạn có thể chọn default sg và thêm 1 rule là allow port 80 .
![architecture-serverless](/workshop-aws-card-clash-1/images/5.fwd/lb2.png)
* Ở phần listeners and routing thì ta chọn protocol http port 80 .
* Target group chọn tg vừa tạo.
![architecture-serverless](/workshop-aws-card-clash-1/images/5.fwd/lb3.png)
* Chọn **Create load balancer**.