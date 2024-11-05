---
title : "Create Primary DB"
date : "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 3.1. </b> "
---
* Search: **RDS**.
* Select: **Create database**.
* Select **Easy create**.
* Select **MySQL**.
* In DB instance size: Select Free Tier.
![primarydb](/workshop-aws-card-clash-1/images/3.connect/rds1.png)

* Name the database: ```database-primary-chatbot```.
* Select self-managed.
* Enter your desired password.
* Select Don't connect to an EC2 compute resource, we will connect later.
![primarydb](/workshop-aws-card-clash-1/images/3.connect/rds2.png)
* Review default settings.
* Select **Create database**.