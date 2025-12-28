# ☁️ Track 3: Cloud & Network Design

[![Duration](https://img.shields.io/badge/Duration-8--10%20weeks-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Intermediate--Advanced-red?style=flat-square)](.)
[![Prerequisites](https://img.shields.io/badge/Prerequisites-Track%201%20%26%202-green?style=flat-square)](../Track2_Orchestration_Automation/)

> **Master Cloud Infrastructure** - AWS, Terraform, Ansible và System Design cho high availability.

---

## 🎯 Mục Tiêu Track

Sau khi hoàn thành Track 3, bạn sẽ có khả năng:

- ✅ Thiết kế và triển khai VPC, subnets, security groups
- ✅ Sử dụng AWS core services (EC2, S3, RDS, IAM)
- ✅ Quản lý databases cho DevOps (MySQL, PostgreSQL, Redis, MongoDB)
- ✅ Configuration management với Ansible
- ✅ Infrastructure as Code với Terraform
- ✅ Thiết kế hệ thống high availability và scalable
- ✅ **Xây dựng full AWS infrastructure với Terraform**

---

## 📋 Prerequisites

Trước khi bắt đầu Track 3, bạn cần hoàn thành:

- ✅ **Track 1 & Track 2**
- ✅ Có AWS Free Tier account
- ✅ Hiểu Kubernetes basics
- ✅ Familiar với YAML configuration

---

## 📚 Danh Sách Modules

| # | Module | Thời Gian | Mô Tả |
|---|--------|-----------|-------|
| 3.1 | [Network Advanced](./3.1_Network_Advanced/) | 1-2 tuần | VPC, Subnets, NAT, Load Balancing |
| 3.2 | [AWS Core Services](./3.2_AWS_Core_Services/) | 2 tuần | EC2, S3, RDS, IAM, CloudWatch |
| 3.3 | [Databases for DevOps](./3.3_Databases_for_DevOps/) | 1-2 tuần | MySQL, PostgreSQL, Redis, MongoDB |
| 3.4 | [Ansible](./3.4_Config_Management_Ansible/) | 1-2 tuần | Playbooks, Roles, Inventory |
| 3.5 | [Terraform](./3.5_Terraform_IaC/) | 2 tuần | HCL, Modules, State, Workspaces |
| 3.6 | [System Design & Reliability](./3.6_System_Design_Reliability/) | 1 tuần | HA, Scalability, Disaster Recovery |
| 3.7 | [**Capstone Project**](./3.7_Capstone_Project/) | 1-2 tuần | 🎯 Production AWS Infrastructure |

---

## 🗓️ Lịch Trình Đề Xuất

### Tuần 1-2: Network Advanced

```
Week 1: VPC fundamentals, subnets, route tables
Week 2: NAT Gateway, VPN, VPC Peering, Load Balancers
```

### Tuần 3-4: AWS Core Services

```
Week 3: EC2, AMI, Auto Scaling Groups
Week 4: S3, RDS, IAM policies, CloudWatch
```

### Tuần 5: Databases for DevOps

```
Day 1-2: MySQL/PostgreSQL administration
Day 3-4: Redis caching strategies
Day 5-7: MongoDB for application data
```

### Tuần 6-7: Ansible

```
Week 6: Ansible basics, playbooks, modules
Week 7: Roles, variables, templates, vault
```

### Tuần 8-9: Terraform

```
Week 8: Terraform fundamentals, resources, providers
Week 9: Modules, state management, workspaces
```

### Tuần 10: System Design + Capstone

```
Day 1-3: HA patterns, scalability, DR strategies
Day 4-7: Capstone implementation
```

---

## 🛠️ Tools Sử Dụng

| Tool | Mục Đích | Documentation |
|------|----------|---------------|
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

Bạn sẽ xây dựng:

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

### Deliverables

- 📁 **Terraform modules** cho VPC, EKS, RDS
- 📜 **Ansible playbooks** cho configuration
- 🔐 **IAM policies** với least privilege
- 📊 **CloudWatch dashboards**
- 📝 **Documentation** và **runbooks**

👉 **[Xem chi tiết Capstone Project →](./3.7_Capstone_Project/)**

---

## 💰 AWS Cost Considerations

> ⚠️ **Chú ý**: AWS resources có thể phát sinh chi phí

### Free Tier Limits

- EC2: 750 hours/month (t2.micro)
- S3: 5GB storage
- RDS: 750 hours/month (db.t2.micro)

### Cost Optimization Tips

1. Luôn **terminate** resources sau khi thực hành
2. Sử dụng **Spot Instances** cho testing
3. Setup **Billing Alerts** trên AWS
4. Dùng **LocalStack** cho local testing

---

## 📊 Đánh Giá

### Tiêu Chí Hoàn Thành Track

- ✅ Hoàn thành tất cả 6 modules
- ✅ Submit Capstone Project với Terraform code
- ✅ Demo working infrastructure on AWS
- ✅ Pass cost review (resources cleaned up)

---

## 🔗 Navigation

| ← Previous | Current | Next → |
|------------|---------|--------|
| [Track 2: Orchestration](../Track2_Orchestration_Automation/) | **Track 3** | [Track 4: DevSecOps](../Track4_DevSecOps/) |

---

## 📖 Bắt Đầu

```bash
# Bắt đầu với Module 3.1
cd 3.1_Network_Advanced
cat README.md
```

**📚 Bắt đầu học:** [3.1 Network Advanced →](./3.1_Network_Advanced/)

---

<div align="center">

**☁️ Welcome to the Cloud! ☁️**

</div>
