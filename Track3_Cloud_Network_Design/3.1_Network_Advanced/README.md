# 🌐 Module 3.1: Network Advanced

[![Duration](https://img.shields.io/badge/Duration-1%20week-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Intermediate-orange?style=flat-square)](.)

> **Advanced Networking** - VPNs, Load Balancing, and Cloud Networking.
>
> *Mạng nâng cao - VPNs, Cân bằng tải, và Mạng đám mây.*

---

## 🎯 Learning Objectives (Mục tiêu học tập)

After this module, you will (Sau module này, bạn sẽ):

- ✅ Understand VPN and Tunneling concepts (Hiểu VPN và Tunneling)
- ✅ Master load balancing strategies (Thành thạo chiến lược cân bằng tải)
- ✅ Design cloud networking - VPC, Subnets (Thiết kế mạng cloud)
- ✅ Implement network security - Security Groups, NACLs (Triển khai bảo mật mạng)
- ✅ Understand CDN and Edge computing (Hiểu CDN và Edge computing)
- ✅ Learn service mesh concepts (Tìm hiểu service mesh)

---

## 📚 Content (Nội dung)

### 1. VPC Architecture (Kiến trúc VPC)

```
┌─────────────────────────────────────────────────────────────┐
│                         VPC (10.0.0.0/16)                   │
│  ┌───────────────────────────────┐ ┌──────────────────────┐ │
│  │  Public Subnet (10.0.1.0/24)  │ │ Public (10.0.2.0/24) │ │
│  │  ┌─────────┐ ┌─────────┐      │ │ ┌─────────┐          │ │
│  │  │   NAT   │ │   ALB   │      │ │ │   NAT   │          │ │
│  │  └─────────┘ └─────────┘      │ │ └─────────┘          │ │
│  └───────────────────────────────┘ └──────────────────────┘ │
│                    │                         │               │
│  ┌───────────────────────────────┐ ┌──────────────────────┐ │
│  │ Private Subnet (10.0.10.0/24) │ │Private (10.0.20.0/24)│ │
│  │  ┌─────────┐ ┌─────────┐      │ │ ┌─────────┐          │ │
│  │  │   EC2   │ │   EC2   │      │ │ │   EC2   │          │ │
│  │  └─────────┘ └─────────┘      │ │ └─────────┘          │ │
│  └───────────────────────────────┘ └──────────────────────┘ │
│                                                              │
│  ┌───────────────────────────────────────────────────────┐  │
│  │              Database Subnet (10.0.100.0/24)          │  │
│  │  ┌─────────┐                  ┌─────────┐             │  │
│  │  │   RDS   │                  │   RDS   │             │  │
│  │  │ Primary │                  │ Standby │             │  │
│  │  └─────────┘                  └─────────┘             │  │
│  └───────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
```

### 2. Load Balancing (Cân bằng tải)

```
            ┌─────────────────────┐
            │   Application LB    │
            │    (Layer 7)        │
            └──────────┬──────────┘
                       │
       ┌───────────────┼───────────────┐
       │               │               │
   ┌───▼───┐       ┌───▼───┐       ┌───▼───┐
   │ App 1 │       │ App 2 │       │ App 3 │
   └───────┘       └───────┘       └───────┘
```

**Load Balancing Algorithms (Thuật toán cân bằng tải):**

- Round Robin (Luân phiên)
- Least Connections (Ít kết nối nhất)
- IP Hash
- Weighted (Có trọng số)

### 3. Security Groups vs NACLs

| Feature (Tính năng) | Security Group | NACL |
|---------------------|----------------|------|
| Level (Cấp độ) | Instance | Subnet |
| State (Trạng thái) | Stateful | Stateless |
| Rules (Quy tắc) | Allow only (Chỉ cho phép) | Allow & Deny (Cho phép & Từ chối) |
| Evaluation (Đánh giá) | All rules (Tất cả rules) | Order matters (Thứ tự quan trọng) |

### 4. VPN Types (Các loại VPN)

- **Site-to-Site VPN**: Connect on-premises to cloud (Kết nối on-premises với cloud)
- **Client VPN**: Remote access for users (Truy cập từ xa cho người dùng)
- **Transit Gateway**: Hub for multiple VPCs (Hub cho nhiều VPCs)

### 5. CDN Concepts (Khái niệm CDN)

```
User → Edge Location → Origin Server
          (Cache)
```

---

## 📝 Module Files (Các file trong Module)

| File | Description |
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

| ← Previous | Current | Next → |
|:------------------:|:------------------:|:-------------:|
| [Track 2 Capstone](../../Track2_Orchestration_Automation/2.6_Capstone_Project/) | **3.1 Network Advanced** | [3.2 AWS Core](../3.2_AWS_Core_Services/) |

---

**Master advanced networking! 🌐**

*Thành thạo mạng nâng cao!*

</div>
