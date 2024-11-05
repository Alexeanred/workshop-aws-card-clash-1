---
title : "Tạo AMI từ instance"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 4.3 </b> "
---

### Tạo AMI instance
Ở instance vừa cấu hình, vào **Actions**: 
* Chọn **Image and templates**, 
* Chọn **Create image**.
![ami1](/workshop-aws-card-clash-1/images/4.s3/ami1.png)
* Đặt tên như: ```final-chatbot-ec2```.
* Description: chatbot streamlit application run on ec2.
* Chọn **Create image**.
![ami2](/workshop-aws-card-clash-1/images/4.s3/ami2.png)
* Tạo thử 1 instance từ AMI đã tạo và chạy thử.