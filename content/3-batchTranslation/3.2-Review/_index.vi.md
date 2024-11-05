---
title : "Tạo Read Replica DB"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 3.2. </b> "
---

* Sau khi tạo xong primary database, ta chọn create read replica từ database đó.

* **Lưu ý**: sau khi có được primary database nằm ở AZ nào, trong read replica ta sẽ chọn AZ khác.
* Ví dụ: primary db sau khi tạo hiển thị us-east-1d thì ta tạo read replica db ở us-east-1a.
* Vào **actions**, chọn **Create read replica**.
![readReplica1](/workshop-aws-card-clash-1/images/3.connect/rr1.png)
* Chọn replica source là primary db.
* Mục DB instance identifier điền tên db: ```database-read-chatbot```.
![readReplica2](/workshop-aws-card-clash-1/images/3.connect/rr2.png)
* Ở Availability chọn single DB instance để tiết kiệm chi phí.
* Ở Availability Zone chọn us-east-1a khác với AZ của primary db.
![readReplica3](/workshop-aws-card-clash-1/images/3.connect/rr3.png)
* Chọn **Create read replica**.