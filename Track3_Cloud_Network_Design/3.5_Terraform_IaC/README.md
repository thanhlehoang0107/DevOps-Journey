# 🏗️ Module 3.5: Terraform IaC

[![Duration](https://img.shields.io/badge/Duration-1%20week-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Intermediate-orange?style=flat-square)](.)

> **Infrastructure as Code** - Manage infrastructure with Terraform.
>
> *Infrastructure as Code - Quản lý hạ tầng với Terraform.*

---

## 🎯 Learning Objectives (Mục tiêu học tập)

After this module, you will (Sau module này, bạn sẽ):

- ✅ Understand Terraform workflow (Hiểu quy trình Terraform)
- ✅ Master HCL syntax (Thành thạo cú pháp HCL)
- ✅ Work with Providers and resources (Làm việc với Providers và resources)
- ✅ Manage Terraform state (Quản lý state)
- ✅ Create reusable modules (Tạo modules tái sử dụng)
- ✅ Use workspaces (Sử dụng workspaces)

---

## 📚 Content (Nội dung)

### 1. Basic Structure (Cấu trúc cơ bản)

```hcl
# main.tf
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
}

provider "aws" {
  region = var.region
}

resource "aws_instance" "web" {
  ami           = var.ami_id
  instance_type = "t3.micro"
  
  tags = {
    Name = "web-server"
  }
}
```

### 2. Variables (Biến)

```hcl
# variables.tf
variable "region" {
  default = "us-east-1"
}

variable "ami_id" {
  type = string
}

# terraform.tfvars
region = "us-west-2"
ami_id = "ami-xxx"
```

### 3. Outputs (Đầu ra)

```hcl
output "instance_ip" {
  value = aws_instance.web.public_ip
}
```

### 4. Commands (Các lệnh)

```bash
terraform init      # Initialize (Khởi tạo)
terraform plan      # Preview changes (Xem trước thay đổi)
terraform apply     # Apply changes (Áp dụng thay đổi)
terraform destroy   # Destroy infrastructure (Hủy hạ tầng)
terraform state list # List resources (Liệt kê resources)
```

### 5. Modules

```hcl
module "vpc" {
  source  = "terraform-aws-modules/vpc/aws"
  version = "5.0.0"
  
  name = "my-vpc"
  cidr = "10.0.0.0/16"
  
  azs             = ["us-east-1a", "us-east-1b"]
  private_subnets = ["10.0.1.0/24", "10.0.2.0/24"]
  public_subnets  = ["10.0.101.0/24", "10.0.102.0/24"]
}
```

---

## 📝 Module Files (Các file trong Module)

| File | Description (Mô tả) |
|------|---------------------|
| [LABS.md](./LABS.md) | Hands-on labs (Bài thực hành) |
| [QUIZ.md](./QUIZ.md) | Knowledge check (Kiểm tra kiến thức) |
| [EXERCISES.md](./EXERCISES.md) | Exercises (Bài tập) |
| [SOLUTIONS.md](./SOLUTIONS.md) | Solutions (Đáp án) |

---

<div align="center">

### 🔗 Module Navigation (Điều hướng Module)

| ← Previous (Trước) | Current (Hiện tại) | Next (Tiếp) → |
|:------------------:|:------------------:|:-------------:|
| [3.4 Ansible](../3.4_Config_Management_Ansible/) | **3.5 Terraform** | [3.6 System Design](../3.6_System_Design_Reliability/) |

---

**Master Infrastructure as Code! 🏗️**

*Thành thạo Infrastructure as Code!*

</div>
