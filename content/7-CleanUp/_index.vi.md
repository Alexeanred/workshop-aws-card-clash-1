---
title : "Dọn dẹp tài nguyên"
date :  "`r Sys.Date()`" 
weight : 7
chapter : false
pre : " <b> 7. </b> "
---
* Xóa Primary database:
![architecture-serverless](/workshop-aws-card-clash-1/images/7.cleanup/asg.png)
* Xóa Auto scaling group:
![architecture-serverless](/workshop-aws-card-clash-1/images/7.cleanup/db.png)
* Xóa Target group:
![architecture-serverless](/workshop-aws-card-clash-1/images/7.cleanup/tg.png)

* Bạn có thể điều chỉnh **desired instances** ở auto scaling group về 0 để asg tự động xóa ec2 instances.

* Xóa replica database.

* Xóa application load balancer.

* Xóa launch template nếu muốn.