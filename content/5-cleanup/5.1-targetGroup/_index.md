---
title : "Create Target Group"
date : "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 5.1 </b> "
---



### Create target group port 8080:
* Go to Target Groups, select **Create Target group**. 
![architecture-serverless](/workshop-aws-card-clash-1/images/5.fwd/tg1.png)
* Target type: Instances.
* Name: ```chatbot-tg```.
* Protocol Port: 8080.
![architecture-serverless](/workshop-aws-card-clash-1/images/5.fwd/tg2.png)
* VPC: select default VPC.
* Health checks section: Select health check port as Override port 8080.
* The remaining parameters are left as default.
![architecture-serverless](/workshop-aws-card-clash-1/images/5.fwd/tg3.png)
* Let's try registering the 2 created targets. 
* Select 2 instances, select ports for selected instances as 8080.
* Select Include as pending below.
* Select the **Create target group** button.
![architecture-serverless](/workshop-aws-card-clash-1/images/5.fwd/tg4.png)