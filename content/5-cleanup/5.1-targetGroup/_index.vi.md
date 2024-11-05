---
title : "Tạo Target Group"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 5.1 </b> "
---



### Tạo target group port 8080:
* Vào mục Target Groups, chọn **Create Target group**. 
![architecture-serverless](/workshop-aws-card-clash-1/images/5.fwd/tg1.png)
* Target type: Instances.
* Name: ```chatbot-tg```.
* Protocol Port: 8080.
![architecture-serverless](/workshop-aws-card-clash-1/images/5.fwd/tg2.png)
* VPC: chọn default VPC.
* Mục health checks: Chọn health check port dạng Override port 8080.
* Các thông số còn lại để default.
![architecture-serverless](/workshop-aws-card-clash-1/images/5.fwd/tg3.png)
* Ta register thử 2 targets đã tạo. 
* Chọn 2 instances, chọn ports for selected instances là 8080.
* Chọn Include as pending below.
* Chọn nút **Create target group**.
![architecture-serverless](/workshop-aws-card-clash-1/images/5.fwd/tg4.png)
