---
title : "Tạo Launch templates"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 6.1 </b> "
---

* Vào Launch templates, chọn **Create launch template**:
![architecture-serverless](/workshop-aws-card-clash-1/images/6.clean/tem1.png)
* Name: ```chatbot-ec2-final-template```
![architecture-serverless](/workshop-aws-card-clash-1/images/6.clean/tem2.png)
* Chọn My AMIs: chọn AMI đã tạo.
* Instance type: chọn t2.micro.
![architecture-serverless](/workshop-aws-card-clash-1/images/6.clean/tem3.png)
* Chọn keypair nếu muốn.
* Subnet: chọn don't include in launch template.
* Ở sg: chọn sg của ec2 instances, sg của ec2-rds-1 (rules để connect ec2 với rds) cho gửi lưu lượng cho sg của rds.
![architecture-serverless](/workshop-aws-card-clash-1/images/6.clean/tem4.png)
* Advanced details thêm IAM instance profile: **ssm-ec2-role**.
![architecture-serverless](/workshop-aws-card-clash-1/images/6.clean/tem5.png)
* Chọn **Create launch template**.


