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
- ✅ Set up CI/CD pipeline with GitHub Actions (Thiết lập CI/CD pipeline)
- ✅ **Deploy a complete static website with automated pipeline** (Deploy website hoàn chỉnh)

---

## 📚 Danh Sách Modules

| # | Module | Thời Gian | Mô Tả |
|---|--------|-----------|-------|
| 1.1 | [Linux & Bash](./1.1_Linux_Bash/) | 1 tuần | Hệ điều hành Linux, command line, Bash scripting |
| 1.2 | [Python Basics](./1.2_Python_Basics/) | 1 tuần | Python fundamentals cho DevOps automation |
| 1.3 | [Network Basics](./1.3_Network_Basics/) | 3-4 ngày | TCP/IP, DNS, HTTP, OSI model |
| 1.4 | [Git & GitHub](./1.4_Git_GitLab/) | 1 tuần | Version control, branching strategies |
| 1.5 | [Docker Fundamentals](./1.5_Docker_Fundamentals/) | 1 tuần | Containers, Dockerfile, Docker images |
| 1.6 | [NGINX Basic](./1.6_NGINX_Basic/) | 3-4 ngày | Web server configuration, reverse proxy |
| 1.7 | [CI/CD Basic](./1.7_CICD_Basic/) | 1 tuần | GitHub Actions, automated workflows |
| 1.8 | [**Capstone Project**](./1.8_Capstone_Project/) | 3-4 ngày | 🎯 Deploy Static Website với CI/CD |

---

## 🗓️ Lịch Trình Đề Xuất

### Tuần 1: Linux & Bash

```
Day 1-2: Linux fundamentals, file system, permissions
Day 3-4: Text processing, pipes, redirects
Day 5-7: Bash scripting, variables, loops, functions
```

### Tuần 2: Python Basics

```
Day 1-2: Data types, control flow
Day 3-4: Functions, modules, file I/O
Day 5-7: Error handling, automation scripts
```

### Tuần 3: Networking + Git

```
Day 1-3: Network fundamentals (OSI, TCP/IP, DNS)
Day 4-7: Git commands, GitHub, branching, PRs
```

### Tuần 4: Docker

```
Day 1-2: Container concepts, Docker basics
Day 3-5: Dockerfile, building images
Day 6-7: Docker Hub, registries
```

### Tuần 5: NGINX + CI/CD

```
Day 1-3: NGINX installation, configuration
Day 4-7: GitHub Actions, workflows, automation
```

### Tuần 6: Capstone Project

```
Day 1-2: Planning, setup repository
Day 3-4: Implement CI/CD pipeline
Day 5-7: Testing, documentation, deployment
```

---

## 🛠️ Tools Sử Dụng

| Tool | Mục Đích | Cài Đặt |
|------|----------|---------|
| **Linux (Ubuntu)** | Operating System | WSL2 / VM / Docker |
| **Bash** | Shell scripting | Built-in |
| **Python 3.x** | Automation scripting | [python.org](https://python.org) |
| **Git** | Version control | [git-scm.com](https://git-scm.com) |
| **Docker** | Containerization | [docker.com](https://docker.com) |
| **NGINX** | Web server | apt/docker |
| **VS Code** | Code editor | [code.visualstudio.com](https://code.visualstudio.com) |
| **GitHub** | Code hosting, CI/CD | [github.com](https://github.com) |

---

## 📋 Prerequisites

Trước khi bắt đầu Track 1, hãy đảm bảo:

- [ ] Đã cài đặt [môi trường phát triển](../Setup_Environment/README.md)
- [ ] Đã tạo tài khoản GitHub
- [ ] Đã cài đặt Docker Desktop
- [ ] Đã cài đặt VS Code với extensions

---

## 🎯 Capstone Project Preview

### **Static Website Deployment với CI/CD Pipeline**

Bạn sẽ xây dựng:

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

👉 **[Xem chi tiết Capstone Project →](./1.8_Capstone_Project/)**

---

## 📊 Đánh Giá

### Tiêu Chí Hoàn Thành Module

| Criteria | Requirement |
|----------|-------------|
| Labs | Hoàn thành 100% hands-on labs |
| Quiz | Đạt ≥ 70% điểm quiz |
| Exercises | Hoàn thành ≥ 80% exercises |
| Project | Submit và được review |

### Tiêu Chí Hoàn Thành Track

- ✅ Hoàn thành tất cả 7 modules
- ✅ Submit Capstone Project
- ✅ Capstone được review và approve

---

## 🔗 Navigation

| ← Previous | Current | Next → |
|------------|---------|--------|
| [Setup Environment](../Setup_Environment/) | **Track 1** | [Track 2: Orchestration](../Track2_Orchestration_Automation/) |

---

## 📖 Bắt Đầu

```bash
# Bắt đầu với Module 1.1
cd 1.1_Linux_Bash
cat README.md
```

**📚 Bắt đầu học:** [1.1 Linux & Bash →](./1.1_Linux_Bash/)

---

<div align="center">

**🚀 Chúc bạn học tốt! 🚀**

</div>
