---
title : "Create IAM role for ec2 instances"
date : "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 2.1 </b> "
---

* We create a Role so that EC2 instance can communicate with other services,
* Create a role with an Amazon Bedrock access policy to use the Claude 3 model or so that the EC2 instance can be managed by AWS Systems Manager.

![test](/workshop-aws-card-clash-1/images/2.prerequisite/image0.png)

* Role analysis:
  * First, the EC2 instance can perform all actions on bedrock
  * Allows description of KMS keys
  * Allows list of roles, access to VPC, subnet, sg.
  * Pass role to be able to use AmazonBedrock related roles.

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
