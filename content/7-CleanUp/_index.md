---
title : "Resource cleanup"
date : "`r Sys.Date()`" 
weight : 7
chapter : false
pre : " <b> 7. </b> "
---
* Delete Primary database:
![architecture-serverless](/workshop-aws-card-clash-1/images/7.cleanup/asg.png)
* Delete Auto scaling group:
![architecture-serverless](/workshop-aws-card-clash-1/images/7.cleanup/db.png)
* Delete Target group:
![architecture-serverless](/workshop-aws-card-clash-1/images/7.cleanup/tg.png)

* You can adjust **desired instances** in auto scaling group to 0 so that asg automatically deletes ec2 instances.

* Delete replica database.

* Delete application load balancer.

* Delete launch template if desired.