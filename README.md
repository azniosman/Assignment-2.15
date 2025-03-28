# Assignment-2.15
Secret Management on AWS

# AWS Secrets Manager Authorization for EC2

## 1. What is needed to authorize your EC2 to retrieve secrets from the AWS Secret Manager?
To authorize an EC2 instance to retrieve secrets from AWS Secrets Manager, you need to:  
- Create an **IAM Role**.  
- Attach the necessary **IAM Policy** to the IAM Role.  
- Associate the IAM Role with the EC2 instance.  
- Grant the role permissions to read specific secrets from AWS Secrets Manager.  

---

## 2. Derived IAM Policy (JSON)
Below is an example IAM policy that allows an EC2 instance to retrieve a specific secret from AWS Secrets Manager:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "secretsmanager:GetSecretValue"
      ],
      "Resource": "arn:aws:secretsmanager:us-east-1:123456789012:secret:prod/cart-service/credentials-*"
    },
    {
      "Effect": "Allow",
      "Action": "secretsmanager:DescribeSecret",
      "Resource": "arn:aws:secretsmanager:us-east-1:123456789012:secret:prod/cart-service/credentials-*"
    }
  ]
}

The ARN for the secret prod/cart-service/credentials would follow this format:
arn:aws:secretsmanager:<region>:<account-id>:secret:prod/cart-service/credentials-*

Example for us-east-1 and account ID 123456789012:
arn:aws:secretsmanager:us-east-1:123456789012:secret:prod/cart-service/credentials-*
