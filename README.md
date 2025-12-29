# 🚀 DevOps Journey

[![GitHub](https://img.shields.io/badge/GitHub-DevOps--Journey-blue?style=flat-square&logo=github)](https://github.com/thanhlehoang0107/DevOps-Journey)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

> **From Zero to DevOps Engineer** - Comprehensive learning path with hands-on labs, real projects, and industry best practices.
>
> *Hành trình từ Zero đến DevOps Engineer - Lộ trình học tập toàn diện với labs thực hành, projects thực tế và best practices.*

---

## 📋 Table of Contents (Mục Lục)

- [Introduction](#-introduction-giới-thiệu)
- [Prerequisites](#-prerequisites-yêu-cầu)
- [Roadmap Structure](#-roadmap-structure-cấu-trúc)
- [Tracks Overview](#-tracks-overview-tổng-quan)
- [Quick Start](#-quick-start)
- [Contributing](#-contributing-đóng-góp)

---

## 🎯 Introduction (Giới Thiệu)

**DevOps Journey** is a comprehensive DevOps learning path, designed for:

*Lộ trình học tập DevOps toàn diện, được thiết kế cho:*

- 🌱 **Beginners** - No IT experience (Người mới bắt đầu)
- 💻 **Developers** - Want to transition to DevOps (Developer muốn chuyển sang DevOps)
- 🔧 **SysAdmins** - Want to improve automation skills (SysAdmin muốn nâng cao kỹ năng)
- 📈 **DevOps Engineers** - Want to strengthen knowledge (Muốn củng cố kiến thức)

### ✨ Key Features (Điểm Nổi Bật)

| Feature | Description |
|---------|-------------|
| 📚 **5 Tracks** | From Foundation to Career Path (Từ nền tảng đến sự nghiệp) |
| 🔬 **Hands-on Labs** | Step-by-step practical exercises (Bài thực hành chi tiết) |
| 🎯 **Capstone Projects** | Real-world projects per Track (Dự án tổng hợp) |
| 📝 **Quizzes** | Knowledge checks (Kiểm tra kiến thức) |
| 📖 **Cheatsheets** | Quick reference guides (Tài liệu tra cứu nhanh) |
| 🛠️ **Real-world Tools** | Docker, Kubernetes, Terraform, AWS... |

---

## 📋 Prerequisites (Yêu Cầu Tiên Quyết)

Before starting, you need to prepare (Trước khi bắt đầu, bạn cần chuẩn bị):

### Phần Cứng

- **RAM**: Tối thiểu 8GB (khuyến nghị 16GB)
- **Storage**: 50GB trống
- **CPU**: 4 cores trở lên

### Phần Mềm

- **OS**: Windows 10/11, macOS, hoặc Linux
- **Git**: Đã cài đặt và cấu hình
- **Docker Desktop**: Đã cài đặt
- **Code Editor**: VS Code (khuyến nghị)
- **Terminal**: PowerShell, Bash hoặc Zsh

### Tài Khoản

- **GitHub Account**: Đã tạo và cấu hình SSH
- **Docker Hub Account**: Để push/pull images
- **AWS Free Tier** (Track 3+): Để thực hành cloud

👉 **[Xem hướng dẫn cài đặt chi tiết →](./Setup_Environment/README.md)**

---

## 🗺️ Cấu Trúc Lộ Trình

```
DevOps-Journey/
├── 📁 Setup_Environment/          # Hướng dẫn cài đặt môi trường
│
├── 📁 Track1_Foundation_StaticWeb/    # 🏗️ Nền tảng & Web tĩnh
│   ├── 1.1_Linux_Bash/
│   ├── 1.2_Python_Basics/
│   ├── 1.3_Network_Basics/
│   ├── 1.4_Git_GitLab/
│   ├── 1.5_Docker_Fundamentals/
│   ├── 1.6_NGINX_Basic/
│   ├── 1.7_CICD_Basic/
│   └── 1.8_Capstone_Project/
│
├── 📁 Track2_Orchestration_Automation/ # ⚙️ Orchestration & Automation
│   ├── 2.1_Docker_Advanced/
│   ├── 2.2_Docker_Compose/
│   ├── 2.3_Jenkins/
│   ├── 2.4_Kubernetes_Core/
│   ├── 2.5_Monitoring_Logging/
│   └── 2.6_Capstone_Project/
│
├── 📁 Track3_Cloud_Network_Design/    # ☁️ Cloud & Infrastructure
│   ├── 3.1_Network_Advanced/
│   ├── 3.2_AWS_Core_Services/
│   ├── 3.3_Databases_for_DevOps/
│   ├── 3.4_Config_Management_Ansible/
│   ├── 3.5_Terraform_IaC/
│   ├── 3.6_System_Design_Reliability/
│   └── 3.7_Capstone_Project/
│
├── 📁 Track4_DevSecOps/               # 🔐 Security
│   ├── 4.1_Security_in_Pipeline/
│   ├── 4.2_Infra_Security/
│   └── 4.3_Capstone_Project/
│
└── 📁 Track5_Career_Path/             # 🎓 Career & Certification
    ├── 5.1_Certifications/
    ├── 5.2_Interview_Prep/
    ├── 5.3_Portfolio_Launch/
    └── 5.4_Grand_Capstone/
```

---

## 📚 Chi Tiết Các Track

### 🏗️ Track 1: Foundation & Static Web
>
> **Thời gian**: 4-6 tuần | **Level**: Beginner

Xây dựng nền tảng vững chắc với Linux, Git, Docker và CI/CD cơ bản.

| Module | Nội Dung | Thời Gian |
|--------|----------|-----------|
| [1.1 Linux & Bash](./Track1_Foundation_StaticWeb/1.1_Linux_Bash/) | Hệ điều hành Linux, Bash scripting | 1 tuần |
| [1.2 Python Basics](./Track1_Foundation_StaticWeb/1.2_Python_Basics/) | Python cho DevOps automation | 1 tuần |
| [1.3 Network Basics](./Track1_Foundation_StaticWeb/1.3_Network_Basics/) | TCP/IP, DNS, HTTP, OSI model | 3-4 ngày |
| [1.4 Git & GitHub](./Track1_Foundation_StaticWeb/1.4_Git_GitLab/) | Version control, branching, Git flow | 1 tuần |
| [1.5 Docker Fundamentals](./Track1_Foundation_StaticWeb/1.5_Docker_Fundamentals/) | Container, Dockerfile, Images | 1 tuần |
| [1.6 NGINX Basic](./Track1_Foundation_StaticWeb/1.6_NGINX_Basic/) | Web server, reverse proxy | 3-4 ngày |
| [1.7 CI/CD Basic](./Track1_Foundation_StaticWeb/1.7_CICD_Basic/) | GitHub Actions fundamentals | 1 tuần |
| [1.8 Capstone](./Track1_Foundation_StaticWeb/1.8_Capstone_Project/) | Deploy Static Website với CI/CD | 3-4 ngày |

👉 **[Bắt đầu Track 1 →](./Track1_Foundation_StaticWeb/README.md)**

---

### ⚙️ Track 2: Orchestration & Automation
>
> **Thời gian**: 6-8 tuần | **Level**: Intermediate

Nâng cao kỹ năng với Docker Compose, Kubernetes và monitoring.

| Module | Nội Dung | Thời Gian |
|--------|----------|-----------|
| [2.1 Docker Advanced](./Track2_Orchestration_Automation/2.1_Docker_Advanced/) | Multi-stage builds, optimization | 1 tuần |
| [2.2 Docker Compose](./Track2_Orchestration_Automation/2.2_Docker_Compose/) | Multi-container applications | 1 tuần |
| [2.3 Jenkins](./Track2_Orchestration_Automation/2.3_Jenkins/) | CI/CD pipelines với Jenkins | 1-2 tuần |
| [2.4 Kubernetes Core](./Track2_Orchestration_Automation/2.4_Kubernetes_Core/) | K8s fundamentals, deployments | 2 tuần |
| [2.5 Monitoring & Logging](./Track2_Orchestration_Automation/2.5_Monitoring_Logging/) | Prometheus, Grafana, ELK | 1-2 tuần |
| [2.6 Capstone](./Track2_Orchestration_Automation/2.6_Capstone_Project/) | Microservices on Kubernetes | 1 tuần |

👉 **[Bắt đầu Track 2 →](./Track2_Orchestration_Automation/README.md)**

---

### ☁️ Track 3: Cloud & Network Design
>
> **Thời gian**: 8-10 tuần | **Level**: Intermediate-Advanced

Master cloud infrastructure với AWS, Terraform và Ansible.

| Module | Nội Dung | Thời Gian |
|--------|----------|-----------|
| [3.1 Network Advanced](./Track3_Cloud_Network_Design/3.1_Network_Advanced/) | VPC, Load Balancing, Security Groups | 1-2 tuần |
| [3.2 AWS Core Services](./Track3_Cloud_Network_Design/3.2_AWS_Core_Services/) | EC2, S3, RDS, IAM | 2 tuần |
| [3.3 Databases for DevOps](./Track3_Cloud_Network_Design/3.3_Databases_for_DevOps/) | MySQL, PostgreSQL, Redis, MongoDB | 1-2 tuần |
| [3.4 Ansible](./Track3_Cloud_Network_Design/3.4_Config_Management_Ansible/) | Configuration management | 1-2 tuần |
| [3.5 Terraform](./Track3_Cloud_Network_Design/3.5_Terraform_IaC/) | Infrastructure as Code | 2 tuần |
| [3.6 System Design](./Track3_Cloud_Network_Design/3.6_System_Design_Reliability/) | High availability, scalability | 1 tuần |
| [3.7 Capstone](./Track3_Cloud_Network_Design/3.7_Capstone_Project/) | Full AWS infrastructure với Terraform | 1-2 tuần |

👉 **[Bắt đầu Track 3 →](./Track3_Cloud_Network_Design/README.md)**

---

### 🔐 Track 4: DevSecOps
>
> **Thời gian**: 4-6 tuần | **Level**: Advanced

Tích hợp security vào DevOps pipeline.

| Module | Nội Dung | Thời Gian |
|--------|----------|-----------|
| [4.1 Security in Pipeline](./Track4_DevSecOps/4.1_Security_in_Pipeline/) | SAST, DAST, Container scanning | 2 tuần |
| [4.2 Infrastructure Security](./Track4_DevSecOps/4.2_Infra_Security/) | Secrets management, compliance | 2 tuần |
| [4.3 Capstone](./Track4_DevSecOps/4.3_Capstone_Project/) | Secure CI/CD pipeline | 1-2 tuần |

👉 **[Bắt đầu Track 4 →](./Track4_DevSecOps/README.md)**

---

### 🎓 Track 5: Career Path
>
> **Thời gian**: 4-6 tuần | **Level**: All

Chuẩn bị sẵn sàng cho career DevOps Engineer.

| Module | Nội Dung | Thời Gian |
|--------|----------|-----------|
| [5.1 Certifications](./Track5_Career_Path/5.1_Certifications/) | AWS, CKA, Terraform Associate | Ongoing |
| [5.2 Interview Prep](./Track5_Career_Path/5.2_Interview_Prep/) | Technical interview, system design | 2 tuần |
| [5.3 Portfolio Launch](./Track5_Career_Path/5.3_Portfolio_Launch/) | GitHub profile, resume, LinkedIn | 1 tuần |
| [5.4 Grand Capstone](./Track5_Career_Path/5.4_Grand_Capstone/) | Production-ready infrastructure | 2-3 tuần |

👉 **[Bắt đầu Track 5 →](./Track5_Career_Path/README.md)**

---

## 📖 Hướng Dẫn Sử Dụng

### Cấu Trúc Mỗi Module

```
Module_Name/
├── README.md          # 📖 Lý thuyết và hướng dẫn chi tiết
├── CHEATSHEET.md      # 📋 Tham khảo nhanh các lệnh
├── LABS.md            # 🔬 Bài thực hành step-by-step
├── QUIZ.md            # ❓ Câu hỏi kiểm tra kiến thức
├── EXERCISES.md       # 💪 Bài tập tự luyện
├── PROJECT.md         # 🎯 Mini project
├── SOLUTIONS.md       # ✅ Đáp án (xem sau khi hoàn thành)
└── images/            # 🖼️ Hình ảnh minh họa
```

### Workflow Học Tập Đề Xuất

```
1. 📖 Đọc README.md     → Hiểu lý thuyết
2. 🔬 Làm LABS.md       → Thực hành theo hướng dẫn
3. 💪 Làm EXERCISES.md  → Tự luyện tập
4. ❓ Làm QUIZ.md       → Test kiến thức
5. 🎯 Làm PROJECT.md    → Áp dụng thực tế
6. 📋 Lưu CHEATSHEET.md → Tham khảo khi cần
7. ✅ Check SOLUTIONS.md → So sánh đáp án
```

---

## 📊 Tiến Độ Học Tập

Sử dụng checklist dưới đây để theo dõi tiến độ:

### Track 1: Foundation & Static Web

- [ ] 1.1 Linux & Bash
- [ ] 1.2 Python Basics
- [ ] 1.3 Network Basics
- [ ] 1.4 Git & GitHub
- [ ] 1.5 Docker Fundamentals
- [ ] 1.6 NGINX Basic
- [ ] 1.7 CI/CD Basic
- [ ] 1.8 Capstone Project

### Track 2: Orchestration & Automation

- [ ] 2.1 Docker Advanced
- [ ] 2.2 Docker Compose
- [ ] 2.3 Jenkins
- [ ] 2.4 Kubernetes Core
- [ ] 2.5 Monitoring & Logging
- [ ] 2.6 Capstone Project

### Track 3: Cloud & Network Design

- [ ] 3.1 Network Advanced
- [ ] 3.2 AWS Core Services
- [ ] 3.3 Databases for DevOps
- [ ] 3.4 Ansible
- [ ] 3.5 Terraform
- [ ] 3.6 System Design & Reliability
- [ ] 3.7 Capstone Project

### Track 4: DevSecOps

- [ ] 4.1 Security in Pipeline
- [ ] 4.2 Infrastructure Security
- [ ] 4.3 Capstone Project

### Track 5: Career Path

- [ ] 5.1 Certifications
- [ ] 5.2 Interview Prep
- [ ] 5.3 Portfolio Launch
- [ ] 5.4 Grand Capstone

---

## 🛠️ Quick Start

```bash
# Clone repository
git clone https://github.com/thanhlehoang0107/DevOps-Journey.git
cd DevOps-Journey

# Bắt đầu với Setup Environment
cd Setup_Environment
cat README.md

# Sau đó bắt đầu Track 1
cd ../Track1_Foundation_StaticWeb/1.1_Linux_Bash
cat README.md
```

---

## 🤝 Đóng Góp

Đóng góp luôn được chào đón! Xem [CONTRIBUTING.md](CONTRIBUTING.md) để biết thêm chi tiết.

### Cách đóng góp

1. Fork repository
2. Tạo branch mới (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Mở Pull Request

---

## 📞 Liên Hệ

- **GitHub**: [@thanhlehoang0107](https://github.com/thanhlehoang0107)
- **Email**: <thanhlehoang0107@gmail.com>

---

## 📄 License

Dự án này được phân phối dưới giấy phép MIT. Xem file [LICENSE](LICENSE) để biết thêm chi tiết.

---

<div align="center">

**⭐ Nếu dự án hữu ích, hãy cho một star! ⭐**

Made with ❤️ by [Thanh Le Hoang](https://github.com/thanhlehoang0107)

</div>
