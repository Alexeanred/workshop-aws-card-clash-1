---
title : "Create RDS instances"
date : "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 3. </b> "
---

### Overview:

* In this architecture, the RDS database acts as a place to store conversations between users and chatbots. 
* We mainly need two operations on this database: READ and WRITE. 
* Therefore, we create the database according to the architecture of 1 primary database and 1 read replica. 
* Primary database has WRITE and READ functions from read replica.

### Content:
- [3.1 Create Primary DB](./3.1-batchJob/)
- [3.2 Create read replica DB](./3.2-Review/)