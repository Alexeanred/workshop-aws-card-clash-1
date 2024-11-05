---
title : "Create Launch templates"
date : "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 6.1 </b> "
---

* Go to Launch templates, select **Create launch template**:
![architecture-serverless](/workshop-aws-card-clash-1/images/6.clean/tem1.png)
* Name: ```chatbot-ec2-final-template```
![architecture-serverless](/workshop-aws-card-clash-1/images/6.clean/tem2.png)
* Select My AMIs: select the created AMI.
* Instance type: select t2.micro.
![architecture-serverless](/workshop-aws-card-clash-1/images/6.clean/tem3.png)
* Select keypair if desired.
* Subnet: select don't include in launch template.
* In sg: select sg of ec2 instances, sg of ec2-rds-1 (rules to connect ec2 with rds) to send traffic to sg of rds.
![architecture-serverless](/workshop-aws-card-clash-1/images/6.clean/tem4.png)
* Advanced details add IAM instance profile: **ssm-ec2-role**.
![architecture-serverless](/workshop-aws-card-clash-1/images/6.clean/tem5.png)
* Select **Create launch template**.