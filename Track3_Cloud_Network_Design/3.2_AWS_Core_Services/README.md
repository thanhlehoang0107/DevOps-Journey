# ☁️ Module 3.2: AWS Core Services

[![Duration](https://img.shields.io/badge/Duration-1--2%20weeks-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Intermediate-orange?style=flat-square)](.)

> **AWS Fundamentals** - Core services cho DevOps trên AWS.

---

## 🎯 Learning Objectives

- ✅ EC2 instances và Auto Scaling
- ✅ S3 storage và policies
- ✅ IAM roles và policies
- ✅ RDS databases
- ✅ Lambda serverless
- ✅ CloudWatch monitoring
- ✅ AWS CLI proficiency

---

## 📚 Content

### 1. EC2

```bash
# Launch EC2
aws ec2 run-instances \
  --image-id ami-xxx \
  --instance-type t3.micro \
  --key-name mykey \
  --security-group-ids sg-xxx \
  --subnet-id subnet-xxx

# Auto Scaling
aws autoscaling create-auto-scaling-group \
  --auto-scaling-group-name my-asg \
  --launch-template LaunchTemplateId=lt-xxx \
  --min-size 1 \
  --max-size 5 \
  --desired-capacity 2 \
  --vpc-zone-identifier "subnet-a,subnet-b"
```

### 2. S3

```bash
# Create bucket
aws s3 mb s3://my-bucket

# Upload
aws s3 cp file.txt s3://my-bucket/

# Sync
aws s3 sync ./folder s3://my-bucket/folder

# Bucket policy
aws s3api put-bucket-policy \
  --bucket my-bucket \
  --policy file://policy.json
```

### 3. IAM

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetObject",
        "s3:PutObject"
      ],
      "Resource": "arn:aws:s3:::my-bucket/*"
    }
  ]
}
```

### 4. Lambda

```python
# lambda_function.py
import json

def lambda_handler(event, context):
    return {
        'statusCode': 200,
        'body': json.dumps('Hello from Lambda!')
    }
```

```bash
aws lambda create-function \
  --function-name my-function \
  --runtime python3.9 \
  --role arn:aws:iam::xxx:role/lambda-role \
  --handler lambda_function.lambda_handler \
  --zip-file fileb://function.zip
```

---

## 📝 Module Files

| File | Description |
|------|-------------|
| [LABS.md](./LABS.md) | Hands-on labs |
| [QUIZ.md](./QUIZ.md) | Knowledge check |
| [EXERCISES.md](./EXERCISES.md) | Exercises |
| [PROJECT.md](./PROJECT.md) | Mini project |
| [SOLUTIONS.md](./SOLUTIONS.md) | Solutions |
| [CHEATSHEET.md](./CHEATSHEET.md) | Quick reference |
