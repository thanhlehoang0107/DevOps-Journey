# 🏗️ Module 3.5: Terraform IaC

> **Infrastructure as Code** - Quản lý infrastructure với Terraform.

---

## 🎯 Learning Objectives

- ✅ Terraform workflow
- ✅ HCL syntax
- ✅ Providers và resources
- ✅ State management
- ✅ Modules
- ✅ Workspaces

---

## 📚 Content

### 1. Basic Structure

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

### 2. Variables

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

### 3. Outputs

```hcl
output "instance_ip" {
  value = aws_instance.web.public_ip
}
```

### 4. Commands

```bash
terraform init      # Initialize
terraform plan      # Preview changes
terraform apply     # Apply changes
terraform destroy   # Destroy infrastructure
terraform state list # List resources
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

## 📝 Module Files

- [LABS.md](./LABS.md) | [QUIZ.md](./QUIZ.md) | [EXERCISES.md](./EXERCISES.md)
