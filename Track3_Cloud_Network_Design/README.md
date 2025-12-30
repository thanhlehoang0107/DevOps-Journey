# ☁️ Track 3: Cloud & Network Design

[![Duration](https://img.shields.io/badge/Duration-8--10%20weeks-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Intermediate--Advanced-red?style=flat-square)](.)
[![Prerequisites](https://img.shields.io/badge/Prerequisites-Track%201%20%26%202-green?style=flat-square)](../Track2_Orchestration_Automation/)

> **Master Cloud Infrastructure** - AWS, Terraform, Ansible, and System Design for high availability.
>
> *Thành thạo Cloud Infrastructure - AWS, Terraform, Ansible và System Design cho high availability.*

---

## 🎯 Track Objectives (Mục Tiêu)

After completing Track 3, you will (Sau khi hoàn thành Track 3, bạn sẽ):

- ✅ Design and deploy VPC, subnets, security groups (Thiết kế và triển khai VPC)
- ✅ Use AWS core services - EC2, S3, RDS, IAM (Sử dụng dịch vụ AWS)
- ✅ Manage databases for DevOps - MySQL, PostgreSQL, Redis (Quản lý databases)
- ✅ Configuration management with Ansible (Quản lý cấu hình với Ansible)
- ✅ Infrastructure as Code with Terraform (IaC với Terraform)
- ✅ Design high availability and scalable systems (Thiết kế hệ thống HA)
- ✅ **Build full AWS infrastructure with Terraform** (Xây dựng hạ tầng AWS)

---

## 📋 Prerequisites (Điều kiện tiên quyết)

Before starting Track 3, you should complete (Trước khi bắt đầu Track 3, bạn cần hoàn thành):

- ✅ **Track 1 & Track 2**
- ✅ Have AWS Free Tier account (Có tài khoản AWS Free Tier)
- ✅ Understand Kubernetes basics (Hiểu K8s cơ bản)
- ✅ Familiar with YAML configuration (Quen thuộc với YAML)

---

## 📚 Module List (Danh Sách Modules)

| # | Module | Duration (Thời gian) | Description (Mô tả) |
|---|--------|----------------------|---------------------|
| 3.1 | [Network Advanced](./3.1_Network_Advanced/) | 1-2 weeks | VPC, Subnets, NAT, Load Balancing |
| 3.2 | [AWS Core Services](./3.2_AWS_Core_Services/) | 2 weeks | EC2, S3, RDS, IAM, CloudWatch |
| 3.3 | [Databases for DevOps](./3.3_Databases_for_DevOps/) | 1-2 weeks | MySQL, PostgreSQL, Redis, MongoDB |
| 3.4 | [Ansible](./3.4_Config_Management_Ansible/) | 1-2 weeks | Playbooks, Roles, Inventory |
| 3.5 | [Terraform](./3.5_Terraform_IaC/) | 2 weeks | HCL, Modules, State, Workspaces |
| 3.6 | [System Design & Reliability](./3.6_System_Design_Reliability/) | 1 week | HA, Scalability, Disaster Recovery |
| 3.7 | [**Capstone Project**](./3.7_Capstone_Project/) | 1-2 weeks | 🎯 Production AWS Infrastructure |

---

## 🗓️ Suggested Schedule (Lịch Trình Đề Xuất)

### Week 1-2: Network Advanced

```
Week 1: VPC fundamentals, subnets, route tables
Week 2: NAT Gateway, VPN, VPC Peering, Load Balancers
```

### Week 3-4: AWS Core Services

```
Week 3: EC2, AMI, Auto Scaling Groups
Week 4: S3, RDS, IAM policies, CloudWatch
```

### Week 5: Databases for DevOps

```
Day 1-2: MySQL/PostgreSQL administration
Day 3-4: Redis caching strategies
Day 5-7: MongoDB for application data
```

### Week 6-7: Ansible

```
Week 6: Ansible basics, playbooks, modules
Week 7: Roles, variables, templates, vault
```

### Week 8-9: Terraform

```
Week 8: Terraform fundamentals, resources, providers
Week 9: Modules, state management, workspaces
```

### Week 10: System Design + Capstone

```
Day 1-3: HA patterns, scalability, DR strategies
Day 4-7: Capstone implementation
```

---

## 🛠️ Tools Used (Công cụ sử dụng)

| Tool | Purpose (Mục đích) | Documentation |
|------|-------------------|---------------|
| **AWS CLI** | AWS command line | [aws.amazon.com/cli](https://aws.amazon.com/cli/) |
| **Terraform** | Infrastructure as Code | [terraform.io](https://www.terraform.io/docs/) |
| **Ansible** | Configuration management | [docs.ansible.com](https://docs.ansible.com/) |
| **MySQL** | Relational database | [dev.mysql.com](https://dev.mysql.com/doc/) |
| **PostgreSQL** | Relational database | [postgresql.org](https://www.postgresql.org/docs/) |
| **Redis** | In-memory cache | [redis.io](https://redis.io/documentation) |
| **MongoDB** | NoSQL database | [mongodb.com](https://docs.mongodb.com/) |

---

## ☁️ AWS Services Covered

### Compute

- **EC2** - Virtual servers
- **Lambda** - Serverless functions
- **ECS/EKS** - Container orchestration

### Storage

- **S3** - Object storage
- **EBS** - Block storage
- **EFS** - File storage

### Database

- **RDS** - Managed relational databases
- **DynamoDB** - NoSQL database
- **ElastiCache** - Managed Redis/Memcached

### Networking

- **VPC** - Virtual Private Cloud
- **Route 53** - DNS
- **CloudFront** - CDN
- **ELB/ALB/NLB** - Load Balancers

### Security

- **IAM** - Identity & Access Management
- **KMS** - Key Management
- **Secrets Manager** - Secrets storage
- **WAF** - Web Application Firewall

### Monitoring

- **CloudWatch** - Metrics & Logs
- **CloudTrail** - API logging
- **X-Ray** - Distributed tracing

---

## 🎯 Capstone Project Preview

### **Production-Ready AWS Infrastructure**

You will build (Bạn sẽ xây dựng):

```
┌─────────────────────────────────────────────────────────────────────┐
│                           AWS Cloud                                 │
│  ┌───────────────────────────────────────────────────────────────┐ │
│  │                        Route 53 (DNS)                         │ │
│  └───────────────────────────────────────────────────────────────┘ │
│                               │                                     │
│                               ▼                                     │
│  ┌───────────────────────────────────────────────────────────────┐ │
│  │                     CloudFront (CDN)                          │ │
│  └───────────────────────────────────────────────────────────────┘ │
│                               │                                     │
│  ┌───────────────────────────────────────────────────────────────┐ │
│  │                           VPC                                 │ │
│  │  ┌─────────────────────────────────────────────────────────┐ │ │
│  │  │                Application Load Balancer                │ │ │
│  │  └─────────────────────────────────────────────────────────┘ │ │
│  │                    │                   │                      │ │
│  │  ┌─────────────────┴───────────────────┴─────────────────┐   │ │
│  │  │              Public Subnets (Multi-AZ)                │   │ │
│  │  │  ┌──────────┐  ┌──────────┐  ┌──────────┐            │   │ │
│  │  │  │ NAT GW   │  │ NAT GW   │  │ Bastion  │            │   │ │
│  │  │  └──────────┘  └──────────┘  └──────────┘            │   │ │
│  │  └───────────────────────────────────────────────────────┘   │ │
│  │                    │                   │                      │ │
│  │  ┌─────────────────┴───────────────────┴─────────────────┐   │ │
│  │  │             Private Subnets (Multi-AZ)                │   │ │
│  │  │  ┌──────────┐  ┌──────────┐  ┌──────────┐            │   │ │
│  │  │  │   EKS    │  │   EKS    │  │   EKS    │            │   │ │
│  │  │  │  Node    │  │  Node    │  │  Node    │            │   │ │
│  │  │  └──────────┘  └──────────┘  └──────────┘            │   │ │
│  │  └───────────────────────────────────────────────────────┘   │ │
│  │                    │                   │                      │ │
│  │  ┌─────────────────┴───────────────────┴─────────────────┐   │ │
│  │  │              Database Subnets (Multi-AZ)              │   │ │
│  │  │  ┌──────────┐  ┌──────────┐  ┌──────────┐            │   │ │
│  │  │  │   RDS    │  │   RDS    │  │  Redis   │            │   │ │
│  │  │  │ Primary  │  │ Replica  │  │ Cluster  │            │   │ │
│  │  │  └──────────┘  └──────────┘  └──────────┘            │   │ │
│  │  └───────────────────────────────────────────────────────┘   │ │
│  └───────────────────────────────────────────────────────────────┘ │
│                                                                     │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐             │
│  │      S3      │  │  CloudWatch  │  │   Secrets    │             │
│  │   Buckets    │  │    Logs      │  │   Manager    │             │
│  └──────────────┘  └──────────────┘  └──────────────┘             │
└─────────────────────────────────────────────────────────────────────┘

                    All managed by Terraform + Ansible
```

### Deliverables (Sản phẩm bàn giao)

- 📁 **Terraform modules** for VPC, EKS, RDS (cho VPC, EKS, RDS)
- 📜 **Ansible playbooks** for configuration (cho cấu hình)
- 🔐 **IAM policies** with least privilege (với quyền tối thiểu)
- 📊 **CloudWatch dashboards**
- 📝 **Documentation** and **runbooks** (Tài liệu và runbooks)

👉 **[View Capstone Details →](./3.7_Capstone_Project/)** | **[Xem chi tiết →](./3.7_Capstone_Project/)**

---

## 💰 AWS Cost Considerations

> ⚠️ **Note (Chú ý)**: AWS resources can incur costs (AWS resources có thể phát sinh chi phí)

### Free Tier Limits (Giới hạn Free Tier)

- EC2: 750 hours/month (t2.micro)
- S3: 5GB storage
- RDS: 750 hours/month (db.t2.micro)

### Cost Optimization Tips (Mẹo tối ưu chi phí)

1. Always **terminate** resources after practice (Luôn terminate resources sau khi thực hành)
2. Use **Spot Instances** for testing (Dùng Spot Instances cho testing)
3. Setup **Billing Alerts** on AWS (Thiết lập Billing Alerts)
4. Use **LocalStack** for local testing (Dùng LocalStack cho local testing)

---

## 📊 Evaluation (Đánh Giá)

### Track Completion Criteria (Tiêu chí hoàn thành Track)

- ✅ Complete all 6 modules (Hoàn thành tất cả 6 modules)
- ✅ Submit Capstone Project with Terraform code
- ✅ Demo working infrastructure on AWS
- ✅ Pass cost review - resources cleaned up (Resources đã dọn dẹp)

---

## 🔗 Navigation

| ← Previous | Current | Next → |
|------------|---------|--------|
| [Track 2: Orchestration](../Track2_Orchestration_Automation/) | **Track 3** | [Track 4: DevSecOps](../Track4_DevSecOps/) |

---

## 📖 Getting Started (Bắt Đầu)

```bash
# Start with Module 3.1 (Bắt đầu với Module 3.1)
cd 3.1_Network_Advanced
cat README.md
```

**📚 Start learning:** [3.1 Network Advanced →](./3.1_Network_Advanced/)

---

<div align="center">

**☁️ Welcome to the Cloud! ☁️**

*Chào mừng đến với Cloud!*

</div>
