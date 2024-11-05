---
title : "Installing EC2 instances"
date : "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 4.1 </b> "
---

# Create ec2 instance
* Name: ```ec2-streamlit-1d```.
* Select AMI: **Amazon Linux 2023 AMI**.
* Select instance type: **t2.micro**.
![ec21](/workshop-aws-card-clash-1/images/4.s3/ec21.png)
* Select key pair if desired.
* Choose default VPC if you want a simple setup or you can use the custom VPC you created.
* Select subnet in AZ: us-east-1d.
* Security Group inbound rules:
    * Since streamlit application runs port 8080, we open port 8080 and source 0.0.0.0/0.
    * Because we need to connect to MySQL, we open port 3306 and source 0.0.0.0/0.
    * Because we need to ssh into the ec2 instance, we open port 22 and source 0.0.0.0/0.
![ec22](/workshop-aws-card-clash-1/images/4.s3/ec22.png)
* In Advanced details, in the IAM instance profile section: select the role you created in the preparation step.
![ec23](/workshop-aws-card-clash-1/images/4.s3/ec23.png)
* Select **Launch instance**.