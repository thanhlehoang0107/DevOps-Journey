# ☁️ Module 3.2: AWS Core Services

[![Duration](https://img.shields.io/badge/Duration-1--2%20weeks-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Intermediate-orange?style=flat-square)](.)

> **AWS Fundamentals** - Core services for DevOps on AWS.
>
> *Nền tảng AWS - Các dịch vụ cốt lõi cho DevOps trên AWS.*

---

## 🎯 Learning Objectives (Mục tiêu học tập)

After this module, you will (Sau module này, bạn sẽ):

- ✅ Launch EC2 instances and Auto Scaling (Khởi chạy EC2 và Auto Scaling)
- ✅ Configure S3 storage and policies (Cấu hình S3 và policies)
- ✅ Manage IAM roles and policies (Quản lý IAM roles và policies)
- ✅ Deploy RDS databases (Deploy databases RDS)
- ✅ Create Lambda serverless functions (Tạo hàm Lambda serverless)
- ✅ Setup CloudWatch monitoring (Thiết lập giám sát CloudWatch)
- ✅ Master AWS CLI (Thành thạo AWS CLI)

---

## 📚 Content (Nội dung)

### 1. EC2

```bash
# Launch EC2 (Khởi chạy EC2)
aws ec2 run-instances \
  --image-id ami-xxx \
  --instance-type t3.micro \
  --key-name mykey \
  --security-group-ids sg-xxx \
  --subnet-id subnet-xxx

# Auto Scaling (Tự động mở rộng)
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
# Create bucket (Tạo bucket)
aws s3 mb s3://my-bucket

# Upload (Tải lên)
aws s3 cp file.txt s3://my-bucket/

# Sync (Đồng bộ)
aws s3 sync ./folder s3://my-bucket/folder

# Bucket policy (Chính sách bucket)
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
# Create function (Tạo hàm)
aws lambda create-function \
  --function-name my-function \
  --runtime python3.9 \
  --role arn:aws:iam::xxx:role/lambda-role \
  --handler lambda_function.lambda_handler \
  --zip-file fileb://function.zip
```

---

## 📝 Module Files (Các file trong Module)

| File | Description (Mô tả) |
|------|---------------------|
| [LABS.md](./LABS.md) | Hands-on labs (Bài thực hành) |
| [QUIZ.md](./QUIZ.md) | Knowledge check (Kiểm tra kiến thức) |
| [EXERCISES.md](./EXERCISES.md) | Exercises (Bài tập) |
| [PROJECT.md](./PROJECT.md) | Mini project (Dự án nhỏ) |
| [SOLUTIONS.md](./SOLUTIONS.md) | Solutions (Đáp án) |
| [CHEATSHEET.md](./CHEATSHEET.md) | Quick reference (Tra cứu nhanh) |

---

<div align="center">

### 🔗 Module Navigation (Điều hướng Module)

| ← Previous (Trước) | Current (Hiện tại) | Next (Tiếp) → |
|:------------------:|:------------------:|:-------------:|
| [3.1 Network Advanced](../3.1_Network_Advanced/) | **3.2 AWS Core** | [3.3 Databases](../3.3_Databases_for_DevOps/) |

---

**Master AWS cloud services! ☁️**

*Thành thạo dịch vụ đám mây AWS!*

</div>
