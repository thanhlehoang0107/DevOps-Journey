# 🏗️ Track 1: Foundation & Static Web

[![Duration](https://img.shields.io/badge/Duration-4--6%20weeks-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Beginner-green?style=flat-square)](.)

> **Build a solid foundation** - From zero to deploying a static website with CI/CD pipeline.
>
> *Xây dựng nền tảng vững chắc - Từ zero đến deploy website tĩnh với CI/CD pipeline.*

---

## 🎯 Track Objectives (Mục Tiêu)

After completing Track 1, you will (Sau khi hoàn thành Track 1, bạn sẽ):

- ✅ Work comfortably with Linux command line and Bash scripting (Làm việc thoải mái với Linux)
- ✅ Write Python scripts for automation tasks (Viết Python scripts tự động hóa)
- ✅ Understand networking fundamentals - TCP/IP, DNS, HTTP (Hiểu networking cơ bản)
- ✅ Use Git & GitHub effectively (Sử dụng Git hiệu quả)
- ✅ Containerize applications with Docker (Container hóa ứng dụng với Docker)
- ✅ Configure NGINX web server (Cấu hình NGINX)
- ✅ Set up CI/CD pipeline with **GitLab CI** (Thiết lập CI/CD pipeline với GitLab CI)
- ✅ **Deploy a complete static website with automated pipeline** (Deploy website hoàn chỉnh)

---

## 📚 Module List (Danh Sách Modules)

| # | Module | Duration | Description |
|---|--------|----------|-------------|
| 1.1 | [Linux & Bash](./1.1_Linux_Bash/) | 1 week | Linux OS, command line, Bash scripting |
| 1.2 | [Python Basics](./1.2_Python_Basics/) | 1 week | Python fundamentals for DevOps automation |
| 1.3 | [Network Basics](./1.3_Network_Basics/) | 3-4 days | TCP/IP, DNS, HTTP, OSI model |
| 1.4 | [Git & GitLab](./1.4_Git_GitLab/) | 1 week | Version control, branching strategies |
| 1.5 | [Docker Fundamentals](./1.5_Docker_Fundamentals/) | 1 week | Containers, Dockerfile, Docker images |
| 1.6 | [NGINX Basic](./1.6_NGINX_Basic/) | 3-4 days | Web server configuration, reverse proxy |
| 1.7 | [CI/CD Basic](./1.7_CICD_Basic/) | 1 week | GitLab CI, automated workflows |
| 1.8 | [**Capstone Project**](./1.8_Capstone_Project/) | 3-4 days | 🎯 Deploy Static Website with CI/CD |

---

## 🗓️ Suggested Schedule (Lịch Trình Đề Xuất)

### Week 1: Linux & Bash

```
Day 1-2: Linux fundamentals, file system, permissions
Day 3-4: Text processing, pipes, redirects
Day 5-7: Bash scripting, variables, loops, functions
```

### Week 2: Python Basics

```
Day 1-2: Data types, control flow
Day 3-4: Functions, modules, file I/O
Day 5-7: Error handling, automation scripts
```

### Week 3: Networking + Git

```
Day 1-3: Network fundamentals (OSI, TCP/IP, DNS)
Day 4-7: Git commands, GitHub, branching, PRs
```

### Week 4: Docker

```
Day 1-2: Container concepts, Docker basics
Day 3-5: Dockerfile, building images
Day 6-7: Docker Hub, registries
```

### Week 5: NGINX + CI/CD

```
Day 1-3: NGINX installation, configuration
Day 4-7: GitLab CI, workflows, automation
```

### Week 6: Capstone Project

```
Day 1-2: Planning, setup repository
Day 3-4: Implement CI/CD pipeline
Day 5-7: Testing, documentation, deployment
```

---

## 🛠️ Tools Used (Công Cụ Sử Dụng)

| Tool | Purpose | Installation |
|------|---------|--------------|
| **Linux (Ubuntu)** | Operating System | WSL2 / VM / Docker |
| **Bash** | Shell scripting | Built-in |
| **Python 3.x** | Automation scripting | [python.org](https://python.org) |
| **Git** | Version control | [git-scm.com](https://git-scm.com) |
| **Docker** | Containerization | [docker.com](https://docker.com) |
| **NGINX** | Web server | apt/docker |
| **VS Code** | Code editor | [code.visualstudio.com](https://code.visualstudio.com) |
| **GitLab** | Code hosting, CI/CD (Primary) | [gitlab.com](https://gitlab.com) |
| **GitHub** | Code hosting (Alternative) | [github.com](https://github.com) |

---

## 📋 Prerequisites (Yêu cầu tiên quyết)

Before starting Track 1, make sure you have (Trước khi bắt đầu, hãy đảm bảo):

- [ ] Installed [development environment](../Setup_Environment/README.md) (Đã cài đặt môi trường)
- [ ] Created GitLab account (Primary) or GitHub account (Đã tạo tài khoản GitLab hoặc GitHub)
- [ ] Installed Docker Desktop (Đã cài đặt Docker Desktop)
- [ ] Installed VS Code with extensions (Đã cài đặt VS Code)

---

## 🎯 Capstone Project Preview

### **Static Website Deployment with CI/CD Pipeline**

You will build (Bạn sẽ xây dựng):

```
┌─────────────────────────────────────────────────────────────┐
│                    GitHub Repository                        │
│  ┌─────────────┐     ┌──────────────┐     ┌──────────────┐ │
│  │   HTML/CSS  │ ──→ │   GitHub     │ ──→ │   Docker     │ │
│  │   Website   │     │   Actions    │     │   Image      │ │
│  └─────────────┘     └──────────────┘     └──────────────┘ │
│                              │                     │        │
│                              ▼                     ▼        │
│                      ┌──────────────┐     ┌──────────────┐ │
│                      │    Tests     │     │  Docker Hub  │ │
│                      │    Lint      │     │    Push      │ │
│                      └──────────────┘     └──────────────┘ │
│                                                    │        │
│                                                    ▼        │
│                                           ┌──────────────┐ │
│                                           │   NGINX      │ │
│                                           │   Deploy     │ │
│                                           └──────────────┘ │
└─────────────────────────────────────────────────────────────┘
```

👉 **[View Capstone Project Details → (Xem chi tiết)](./1.8_Capstone_Project/)**

---

## 📊 Assessment (Đánh Giá)

### Module Completion Criteria (Tiêu Chí Hoàn Thành Module)

| Criteria | Requirement |
|----------|-------------|
| Labs | Complete 100% hands-on labs |
| Quiz | Score ≥ 70% on quiz |
| Exercises | Complete ≥ 80% exercises |
| Project | Submit and reviewed |

### Track Completion Criteria (Tiêu Chí Hoàn Thành Track)

- ✅ Complete all 7 modules (Hoàn thành tất cả 7 modules)
- ✅ Submit Capstone Project
- ✅ Capstone reviewed and approved

---

## 🔗 Navigation

| ← Previous | Current | Next → |
|------------|---------|--------|
| [Setup Environment](../Setup_Environment/) | **Track 1** | [Track 2: Orchestration](../Track2_Orchestration_Automation/) |

---

## 📖 Getting Started (Bắt Đầu)

```bash
# Start with Module 1.1 (Bắt đầu với Module 1.1)
cd 1.1_Linux_Bash
cat README.md
```

**📚 Start Learning (Bắt đầu học):** [1.1 Linux & Bash →](./1.1_Linux_Bash/)

---

<div align="center">

**🚀 Good luck with your learning! 🚀**

*Chúc bạn học tốt!*

</div>
