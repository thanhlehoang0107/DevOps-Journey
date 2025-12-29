# 🏆 Module 2.6: Capstone Project

> **Microservices on Kubernetes with CI/CD and Monitoring**
>
> *Microservices trên Kubernetes với CI/CD và Monitoring*

---

## 🎯 Project Overview (Tổng quan dự án)

Combine all Track 2 knowledge to deploy a production-ready microservices platform.

*Tổng hợp tất cả kiến thức Track 2 để deploy nền tảng microservices production-ready.*

---

## 📋 Requirements (Yêu cầu)

### Architecture (Kiến trúc)

```
┌──────────────────────────────────────────────────────────────┐
│                         Kubernetes                            │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────────────┐   │
│  │  Frontend   │  │  API Gateway│  │   Backend Services  │   │
│  │  (React)    │──│   (NGINX)   │──│  - Auth Service     │   │
│  └─────────────┘  └─────────────┘  │  - User Service     │   │
│                                    │  - Order Service    │   │
│                                    └─────────────────────┘   │
│                                              │                │
│                    ┌─────────────────────────┼───────┐       │
│                    │                         │       │       │
│              ┌─────▼─────┐  ┌───────────┐  ┌─▼───┐   │       │
│              │ PostgreSQL│  │   Redis   │  │ RabbitMQ│       │
│              └───────────┘  └───────────┘  └─────┘   │       │
│                                                      │       │
│  ┌─────────────────────────────────────────────────┐│       │
│  │              Monitoring Stack                    ││       │
│  │  Prometheus │ Grafana │ Loki │ Alertmanager     ││       │
│  └─────────────────────────────────────────────────┘│       │
└──────────────────────────────────────────────────────┘       │
                              │                                 │
                    ┌─────────▼─────────┐                      │
                    │    Jenkins CI/CD   │                      │
                    └───────────────────┘                      │
```

### Deliverables (Sản phẩm bàn giao)

#### 1. Application - Docker Images (Ứng dụng)

- [ ] Frontend container (< 50MB)
- [ ] Backend services with multi-stage builds (Backend với multi-stage builds)
- [ ] All images pushed to registry (Tất cả images đã push lên registry)

#### 2. Kubernetes Manifests

- [ ] Deployments with health checks (Deployments với health checks)
- [ ] Services (ClusterIP, LoadBalancer)
- [ ] ConfigMaps & Secrets
- [ ] PersistentVolumeClaims
- [ ] HorizontalPodAutoscaler

#### 3. CI/CD Pipeline

- [ ] Jenkins/GitHub Actions pipeline
- [ ] Automated testing (Test tự động)
- [ ] Docker build & push
- [ ] Kubernetes deployment
- [ ] Rollback capability (Khả năng rollback)

#### 4. Monitoring (Giám sát)

- [ ] Prometheus scraping all services
- [ ] Grafana dashboards (minimum 3) (Tối thiểu 3 dashboard)
- [ ] Alert rules configured (Đã cấu hình cảnh báo)
- [ ] Logging with Loki (Logging với Loki)

---

## 📁 Project Structure (Cấu trúc dự án)

```
capstone-project/
├── apps/
│   ├── frontend/
│   │   ├── Dockerfile
│   │   └── src/
│   ├── auth-service/
│   │   ├── Dockerfile
│   │   └── src/
│   └── user-service/
│       ├── Dockerfile
│       └── src/
├── k8s/
│   ├── base/
│   │   ├── deployments/
│   │   ├── services/
│   │   └── kustomization.yaml
│   ├── staging/
│   └── production/
├── monitoring/
│   ├── prometheus/
│   ├── grafana/
│   └── docker-compose.yml
├── ci/
│   ├── Jenkinsfile
│   └── .github/workflows/
└── README.md
```

---

## ✅ Acceptance Criteria (Tiêu chí chấp nhận)

| Requirement (Yêu cầu) | Weight (Trọng số) |
|-----------------------|-------------------|
| All services running on K8s (Tất cả services chạy trên K8s) | 25% |
| CI/CD pipeline working (Pipeline CI/CD hoạt động) | 25% |
| Monitoring stack (Stack giám sát) | 20% |
| Documentation (Tài liệu) | 15% |
| Security best practices (Bảo mật) | 15% |

---

## 📊 Evaluation (Đánh giá)

| Grade (Xếp loại) | Score (Điểm) |
|------------------|--------------|
| Excellent (Xuất sắc) | 90-100% |
| Good (Tốt) | 75-89% |
| Pass (Đạt) | 60-74% |
| Fail (Không đạt) | < 60% |

---

## 🚀 Getting Started (Bắt đầu)

1. Setup Kubernetes cluster - minikube/kind (Thiết lập cluster Kubernetes)
2. Deploy base infrastructure (Deploy hạ tầng cơ bản)
3. Build and deploy applications (Build và deploy ứng dụng)
4. Setup CI/CD (Thiết lập CI/CD)
5. Configure monitoring (Cấu hình giám sát)
6. Document everything (Viết tài liệu)

---

<div align="center">

### 🔗 Module Navigation (Điều hướng Module)

| ← Previous | Current | Next → |
|:------------------:|:------------------:|:-------------:|
| [2.5 Monitoring](../2.5_Monitoring_Logging/) | **2.6 Capstone** | [Track 3](../../Track3_Cloud_Network_Design/) |

---

**Good luck with your capstone! 🏆**

*Chúc may mắn với dự án tổng hợp!*

</div>
