---
title : "Create Application Load Balancer"
date : "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 5.2 </b> "
---
* Go to **Load Balancers**:
* Select **Create Load balancer**.
* Select **Application Load Balancer**.
![architecture-serverless](/workshop-aws-card-clash-1/images/5.fwd/lb1.png)
* Name: ```chatbot-alb```
* Select Scheme: internet-facing.
* Select IP address type: IPv4.
* Select VPC default.
* AZs: select 2 AZs us-east-1a and us-east-1d.
* For security group you can choose default sg and add a rule to allow port 80.
![architecture-serverless](/workshop-aws-card-clash-1/images/5.fwd/lb2.png)
* In the listeners and routing section, we choose protocol http port 80.
* Target group selects the newly created group.
![architecture-serverless](/workshop-aws-card-clash-1/images/5.fwd/lb3.png)
* Select **Create load balancer**.