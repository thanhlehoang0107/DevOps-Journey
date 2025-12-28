# ⚙️ Track 2: Orchestration & Automation

[![Duration](https://img.shields.io/badge/Duration-6--8%20weeks-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Intermediate-orange?style=flat-square)](.)
[![Prerequisites](https://img.shields.io/badge/Prerequisites-Track%201-green?style=flat-square)](../Track1_Foundation_StaticWeb/)

> **Nâng cao kỹ năng DevOps** - Master Docker Compose, Kubernetes, Jenkins và Monitoring stack.

---

## 🎯 Mục Tiêu Track

Sau khi hoàn thành Track 2, bạn sẽ có khả năng:

- ✅ Xây dựng multi-container applications với Docker Compose
- ✅ Tối ưu hóa Docker images (multi-stage builds, caching)
- ✅ Thiết lập CI/CD pipelines với Jenkins
- ✅ Deploy và quản lý applications trên Kubernetes
- ✅ Implement monitoring với Prometheus & Grafana
- ✅ Centralized logging với ELK Stack
- ✅ **Deploy microservices architecture trên Kubernetes cluster**

---

## 📋 Prerequisites

Trước khi bắt đầu Track 2, bạn cần hoàn thành:

- ✅ **Track 1: Foundation & Static Web**
- ✅ Hiểu Docker fundamentals
- ✅ Có kinh nghiệm với GitHub Actions
- ✅ Familiar với Linux command line

---

## 📚 Danh Sách Modules

| # | Module | Thời Gian | Mô Tả |
|---|--------|-----------|-------|
| 2.1 | [Docker Advanced](./2.1_Docker_Advanced/) | 1 tuần | Multi-stage builds, optimization, security |
| 2.2 | [Docker Compose](./2.2_Docker_Compose/) | 1 tuần | Multi-container apps, networking, volumes |
| 2.3 | [Jenkins](./2.3_Jenkins/) | 1-2 tuần | CI/CD pipelines, Jenkinsfile, plugins |
| 2.4 | [Kubernetes Core](./2.4_Kubernetes_Core/) | 2 tuần | Pods, Deployments, Services, Ingress |
| 2.5 | [Monitoring & Logging](./2.5_Monitoring_Logging/) | 1-2 tuần | Prometheus, Grafana, ELK Stack |
| 2.6 | [**Capstone Project**](./2.6_Capstone_Project/) | 1 tuần | 🎯 Microservices on Kubernetes |

---

## 🗓️ Lịch Trình Đề Xuất

### Tuần 1: Docker Advanced

```
Day 1-2: Multi-stage builds, build optimization
Day 3-4: Docker networking deep dive
Day 5-7: Security best practices, scanning
```

### Tuần 2: Docker Compose

```
Day 1-2: Compose fundamentals, services
Day 3-4: Networking, volumes, dependencies
Day 5-7: Environment management, overrides
```

### Tuần 3-4: Jenkins

```
Week 3: Jenkins setup, basic pipelines
Week 4: Advanced pipelines, shared libraries, agents
```

### Tuần 5-6: Kubernetes Core

```
Week 5: K8s architecture, Pods, Deployments
Week 6: Services, Ingress, ConfigMaps, Secrets
```

### Tuần 7: Monitoring & Logging

```
Day 1-3: Prometheus setup, metrics collection
Day 4-5: Grafana dashboards
Day 6-7: ELK Stack, log aggregation
```

### Tuần 8: Capstone Project

```
Day 1-2: Architecture design
Day 3-5: Implementation
Day 6-7: Testing, documentation
```

---

## 🛠️ Tools Sử Dụng

| Tool | Mục Đích | Documentation |
|------|----------|---------------|
| **Docker Compose** | Multi-container orchestration | [docs.docker.com](https://docs.docker.com/compose/) |
| **Jenkins** | CI/CD automation server | [jenkins.io](https://www.jenkins.io/doc/) |
| **Kubernetes** | Container orchestration | [kubernetes.io](https://kubernetes.io/docs/) |
| **Minikube/Kind** | Local K8s cluster | [minikube.sigs.k8s.io](https://minikube.sigs.k8s.io/) |
| **kubectl** | K8s CLI | [kubernetes.io/docs/reference/kubectl](https://kubernetes.io/docs/reference/kubectl/) |
| **Prometheus** | Metrics & alerting | [prometheus.io](https://prometheus.io/docs/) |
| **Grafana** | Visualization | [grafana.com](https://grafana.com/docs/) |
| **Elasticsearch** | Log storage | [elastic.co](https://www.elastic.co/guide/) |
| **Fluentd/Filebeat** | Log collection | [fluentd.org](https://docs.fluentd.org/) |
| **Kibana** | Log visualization | [elastic.co](https://www.elastic.co/guide/en/kibana/) |

---

## 🎯 Capstone Project Preview

### **Microservices Deployment on Kubernetes**

Bạn sẽ xây dựng:

```
┌─────────────────────────────────────────────────────────────────────┐
│                     Kubernetes Cluster                              │
│  ┌──────────────────────────────────────────────────────────────┐  │
│  │                        Ingress Controller                     │  │
│  └──────────────────────────────────────────────────────────────┘  │
│                               │                                     │
│         ┌─────────────────────┼─────────────────────┐              │
│         │                     │                     │              │
│         ▼                     ▼                     ▼              │
│  ┌─────────────┐      ┌─────────────┐      ┌─────────────┐        │
│  │  Frontend   │      │   API       │      │   Auth      │        │
│  │  Service    │ ───▶ │   Gateway   │ ───▶ │   Service   │        │
│  └─────────────┘      └─────────────┘      └─────────────┘        │
│                               │                                     │
│         ┌─────────────────────┼─────────────────────┐              │
│         │                     │                     │              │
│         ▼                     ▼                     ▼              │
│  ┌─────────────┐      ┌─────────────┐      ┌─────────────┐        │
│  │   User      │      │   Product   │      │   Order     │        │
│  │   Service   │      │   Service   │      │   Service   │        │
│  └─────────────┘      └─────────────┘      └─────────────┘        │
│         │                     │                     │              │
│         └─────────────────────┼─────────────────────┘              │
│                               ▼                                     │
│                      ┌─────────────┐                               │
│                      │  Database   │                               │
│                      │  (MongoDB)  │                               │
│                      └─────────────┘                               │
│                                                                     │
│  ┌──────────────────────────────────────────────────────────────┐  │
│  │           Monitoring Stack (Prometheus + Grafana)            │  │
│  └──────────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────────┘
```

### Features

- 🔄 **CI/CD Pipeline** với Jenkins
- 🐳 **Containerized** microservices
- ☸️ **Kubernetes** deployment
- 📊 **Monitoring** với Prometheus & Grafana
- 📝 **Logging** với ELK Stack
- 🔐 **Secrets management** với K8s Secrets

👉 **[Xem chi tiết Capstone Project →](./2.6_Capstone_Project/)**

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

- ✅ Hoàn thành tất cả 5 modules
- ✅ Submit Capstone Project
- ✅ Demo microservices running on K8s

---

## 🔗 Navigation

| ← Previous | Current | Next → |
|------------|---------|--------|
| [Track 1: Foundation](../Track1_Foundation_StaticWeb/) | **Track 2** | [Track 3: Cloud](../Track3_Cloud_Network_Design/) |

---

## 📖 Bắt Đầu

```bash
# Bắt đầu với Module 2.1
cd 2.1_Docker_Advanced
cat README.md
```

**📚 Bắt đầu học:** [2.1 Docker Advanced →](./2.1_Docker_Advanced/)

---

<div align="center">

**🚀 Level up your DevOps skills! 🚀**

</div>
