---
title : "Tạo IAM role cho ec2 instances"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 2.1 </b> "
---

* Ta tạo Role để EC2 instance có thể giao tiếp với các services khác,
* Tạo role có policy truy cập Amazon Bedrock để dùng model Claude 3 hay để EC2 instance có thể được quản lý bởi AWS Systems Manager.

![test](/workshop-aws-card-clash-1/images/2.prerequisite/image0.png)

* Phân tích role:
  * Đầu tiên là EC2 instance có thể thực hiện tất cả hành động trên bedrock
  * Cho phép mô tả các khóa KMS
  * Cho phép list các roles, truy cập vào VPC, subnet, sg.
  * Pass role để có thể sử dụng những role liên quan AmazonBedrock.
```yaml
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "BedrockAll",
            "Effect": "Allow",
            "Action": [
                "bedrock:*"
            ],
            "Resource": "*"
        },
        {
            "Sid": "DescribeKey",
            "Effect": "Allow",
            "Action": [
                "kms:DescribeKey"
            ],
            "Resource": "arn:*:kms:*:::*"
        },
        {
            "Sid": "APIsWithAllResourceAccess",
            "Effect": "Allow",
            "Action": [
                "iam:ListRoles",
                "ec2:DescribeVpcs",
                "ec2:DescribeSubnets",
                "ec2:DescribeSecurityGroups"
            ],
            "Resource": "*"
        },
        {
            "Sid": "PassRoleToBedrock",
            "Effect": "Allow",
            "Action": [
                "iam:PassRole"
            ],
            "Resource": "arn:aws:iam::*:role/*AmazonBedrock*",
            "Condition": {
                "StringEquals": {
                    "iam:PassedToService": [
                        "bedrock.amazonaws.com"
                    ]
                }
            }
        }
    ]
}
```