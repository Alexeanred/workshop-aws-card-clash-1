---
title : "Create ASG"
date : "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 6.2 </b> "
---

* Go to **Auto groups scaling**:
1. Step 1:
    * Name: ```asg-chatbot```.
    * Launch template: select the newly created template.
![architecture-serverless](/workshop-aws-card-clash-1/images/6.clean/asg1.png)
2. Step 2:
    * Select vpc default.
    * Select subnet as 2 subnets us-east-1d and us-east-1a.
![architecture-serverless](/workshop-aws-card-clash-1/images/6.clean/asg2.png)
3. Step 3:
    * In Load balancing: select Attach to an existing load balancer.
    * Select the created target group.
![architecture-serverless](/workshop-aws-card-clash-1/images/6.clean/asg3.png)
4. Step 4:
    * Group size:
    * Select desired capacity as 2.
    * Min: 0 and Max: 3.
![architecture-serverless](/workshop-aws-card-clash-1/images/6.clean/asg4.png)
5. Step 5: 
    * Can add notifications:
    * SNS topics:
    * Give your name and fill in your email.
![architecture-serverless](/workshop-aws-card-clash-1/images/6.clean/asg5.png)
* Review again and select **Create Auto Scaling Group**.
![architecture-serverless](/workshop-aws-card-clash-1/images/6.clean/asg6.png)