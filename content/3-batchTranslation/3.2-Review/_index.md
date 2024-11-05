---
title : "Create Read Replica DB"
date : "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 3.2. </b> "
---

* After creating the primary database, we choose to create read replica from that database.

* **Note**: after knowing which AZ the primary database is located in, in read replica we will choose another AZ.
* For example: after creating a primary database displaying us-east-1d, we create a read replica db in us-east-1a.
* Go to **actions**, select **Create read replica**.
![readReplica1](/workshop-aws-card-clash-1/images/3.connect/rr1.png)
* Select replica source as primary database.
* The DB instance identifier section fills in the db name: ```database-read-chatbot```.
![readReplica2](/workshop-aws-card-clash-1/images/3.connect/rr2.png)
* In Availability, choose single DB instance to save costs.
* In Availability Zone, select us-east-1a which is different from the AZ of the primary database.
![readReplica3](/workshop-aws-card-clash-1/images/3.connect/rr3.png)
* Select **Create read replica**.