---
title : "Tạo ASG"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 6.2 </b> "
---

* Vào **Auto scaling groups**:
1. Step 1:
    * Name: ```asg-chatbot```.
    * Launch template: chọn template vừa tạo.
![architecture-serverless](/workshop-aws-card-clash-1/images/6.clean/asg1.png)
2. Step 2:
    * Chọn vpc default.
    * Chọn subnet là 2 subnets us-east-1d và us-east-1a.
![architecture-serverless](/workshop-aws-card-clash-1/images/6.clean/asg2.png)
3. Step 3:
    * Trong Load balancing: chọn Attach to an existing load balancer.
    * Chọn target group đã tạo.
![architecture-serverless](/workshop-aws-card-clash-1/images/6.clean/asg3.png)
4. Step 4:
    * Group size:
    * Chọn desired capacity là 2.
    * Min: 0 và Max: 3.
![architecture-serverless](/workshop-aws-card-clash-1/images/6.clean/asg4.png)
5. Step 5: 
    * Có thể add notifications:
    * SNS topic:
    * Đặt tên và điền email.
![architecture-serverless](/workshop-aws-card-clash-1/images/6.clean/asg5.png)
* Review lại và chọn **Create Auto Scaling Group**.
![architecture-serverless](/workshop-aws-card-clash-1/images/6.clean/asg6.png)