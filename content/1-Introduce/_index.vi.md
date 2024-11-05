---
title : "Giới thiệu"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---
![arch](/workshop-aws-card-clash-1/images/arc1.png) 
## Ý tưởng kiến trúc: 
* **Mục tiêu**: Xây dựng một trang web cho phép người dùng giao tiếp với chatbot thông qua kiến trúc đảm bảo tính High Availability (HA) và Scalable.
* **Quy trình**:
    * **Streamlit Application**: Được sử dụng làm giao diện người dùng, nơi người dùng có thể gửi câu hỏi.
    * **API Amazon Bedrock**: Kết nối với API của mô hình Claude 3 Sonnet từ Amazon Bedrock để xử lý các câu hỏi và cung cấp câu trả lời.
    * **Application Load Balancer (ALB)**: Đảm bảo phân phối lưu lượng truy cập đến các instance EC2 để giảm tải và đảm bảo ứng dụng luôn sẵn sàng.
    * **Auto Scaling Group (ASG)**: Tự động quản lý số lượng EC2 instances, giúp đáp ứng linh hoạt theo nhu cầu thực tế.
    * **AWS RDS với Read Replica**: Lưu trữ và quản lý cuộc trò chuyện, đảm bảo hiệu suất và khả năng chịu tải của cơ sở dữ liệu.
### Giao diện ứng dụng
![arch](/workshop-aws-card-clash-1/images/image.png) 
## Giới thiệu dịch vụ:
**Amazon Bedrock**: Dịch vụ cho phép dễ dàng tích hợp các mô hình ngôn ngữ tổng hợp tiên tiến (LLM) vào ứng dụng, giúp xây dựng chatbot, hệ thống gợi ý và các ứng dụng AI khác một cách nhanh chóng và linh hoạt.

**Amazon EC2**: Dịch vụ cung cấp các máy chủ ảo (instances) để chạy ứng dụng, cho phép dễ dàng thay đổi kích thước và cấu hình tài nguyên theo nhu cầu.

**AWS RDS**: Dịch vụ cơ sở dữ liệu được quản lý, hỗ trợ nhiều hệ quản trị cơ sở dữ liệu như MySQL, PostgreSQL, giúp giảm tải công việc quản trị và tối ưu hóa hiệu suất.

**Amazon ALB**: Application Load Balancer, dịch vụ cân bằng tải ứng dụng, giúp phân phối lưu lượng truy cập đến nhiều instance EC2, đảm bảo tính sẵn sàng và khả năng mở rộng của ứng dụng.

**AWS Auto Scaling Group**: Dịch vụ tự động điều chỉnh số lượng instance EC2 theo nhu cầu, giúp đảm bảo hiệu suất ổn định và tối ưu hóa chi phí.
