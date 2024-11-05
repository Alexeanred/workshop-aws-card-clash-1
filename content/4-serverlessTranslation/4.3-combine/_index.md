---
title : "Create AMI from instance"
date : "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 4.3 </b> "
---

### Create AMI instance
In the newly configured instance, go to **Actions**: 
* Select **Image and templates**, 
* Select **Create image**.
![ami1](/workshop-aws-card-clash-1/images/4.s3/ami1.png)
* Name it like: ```final-chatbot-ec2```.
* Description: chatbot streamlit application run on ec2.
* Select **Create image**.
![ami2](/workshop-aws-card-clash-1/images/4.s3/ami2.png)
* Create a test instance from the created AMI and test it.