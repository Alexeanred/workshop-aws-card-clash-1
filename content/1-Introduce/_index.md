---
title : "Introduction"
date : "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---
![arch](/workshop-aws-card-clash-1/images/arc1.png) 
## Architectural ideas: 
* **Goal**: Build a website that allows users to communicate with chatbots through an architecture that ensures High Availability (HA) and Scalability.
* **Procedure**:
    * **Streamlit Application**: Used as a user interface where users can submit questions.
    * **Amazon Bedrock API**: Connects to the Claude 3 Sonnet model API from Amazon Bedrock to process questions and provide answers.
    * **Application Load Balancer (ALB)**: Ensures traffic distribution to EC2 instances to reduce load and ensure application availability.
    * **Auto Scaling Group (ASG)**: Automatically manages the number of EC2 instances, helping to flexibly respond to actual needs.
    * **AWS RDS with Read Replica**: Stores and manages conversations, ensuring database performance and load capacity.
### App Interface
![arch](/workshop-aws-card-clash-1/images/image.png) 
## Service introduction:
**Amazon Bedrock**: Service that allows easy integration of advanced synthetic language models (LLM) into applications, helping to quickly build chatbots, recommendation systems and other AI applications and flexible.

**Amazon EC2**: Service that provides virtual servers (instances) to run applications, allowing easy resizing and configuration of resources according to needs.

**AWS RDS**: Managed database service, supporting many database management systems such as MySQL, PostgreSQL, helping to reduce administrative work and optimize performance.

**Amazon ALB**: Application Load Balancer, an application load balancing service, helps distribute traffic to multiple EC2 instances, ensuring application availability and scalability.

**AWS Auto Scaling Group**: Service that automatically adjusts the number of EC2 instances according to demand, helping to ensure stable performance and optimize costs.