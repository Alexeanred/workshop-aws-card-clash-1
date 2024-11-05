---
title : "Tạo RDS instances"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 3. </b> "
---

### Tổng quan:

* Trong kiến trúc này, RDS database đóng vai trò là một nơi lưu trữ những cuộc trò chuyện giữa người dùng và chatbot. 
* Ta cần chủ yếu 2 hoạt động trên database này là READ và WRITE. 
* Vì thế, ta tạo database theo kiến trúc 1 primary database và 1 read replica. 
* Primary database có chức năng WRITE và READ từ read replica.

### Nội dung:
- [3.1 Tạo Primary DB](./3.1-batchJob/)
- [3.2 Tạo read replica DB](./3.2-Review/)
