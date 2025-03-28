# Assignment-2.15
Secret Management on AWS

## EC2 Secrets Manager Authorization

**What is needed to authorize your EC2 to retrieve secrets from the AWS Secret Manager?**

To authorize your EC2 instance to retrieve secrets from AWS Secrets Manager, you need to grant it the necessary permissions. This is typically done by attaching an **IAM role** to the EC2 instance. This role will contain a policy that allows the EC2 instance to perform the `secretsmanager:GetSecretValue` action on the specific secrets it needs to access.

**Derive the IAM policy (i.e. JSON)?**

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "secretsmanager:GetSecretValue"
            ],
            "Resource": "arn:aws:secretsmanager:ap-southeast-1:YOUR_ACCOUNT_ID:secret:prod/cart-service/credentials-RANDOM_STRING"
        }
    ]
}
