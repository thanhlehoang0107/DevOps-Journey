# 🏆 Module 2.6: Capstone Project

> **Microservices trên Kubernetes với CI/CD và Monitoring**

---

## 🎯 Project Overview

Tổng hợp tất cả kiến thức Track 2 để deploy production-ready microservices platform.

---

## 📋 Requirements

### Architecture

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

### Deliverables

#### 1. Application (Docker Images)

- [ ] Frontend container (< 50MB)
- [ ] Backend services (multi-stage builds)
- [ ] All images pushed to registry

#### 2. Kubernetes Manifests

- [ ] Deployments với health checks
- [ ] Services (ClusterIP, LoadBalancer)
- [ ] ConfigMaps & Secrets
- [ ] PersistentVolumeClaims
- [ ] HorizontalPodAutoscaler

#### 3. CI/CD Pipeline

- [ ] Jenkins/GitHub Actions pipeline
- [ ] Automated testing
- [ ] Docker build & push
- [ ] Kubernetes deployment
- [ ] Rollback capability

#### 4. Monitoring

- [ ] Prometheus scraping all services
- [ ] Grafana dashboards (3 minimum)
- [ ] Alert rules configured
- [ ] Logging với Loki

---

## 📁 Project Structure

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

## ✅ Acceptance Criteria

| Requirement | Weight |
|-------------|--------|
| All services running on K8s | 25% |
| CI/CD pipeline working | 25% |
| Monitoring stack | 20% |
| Documentation | 15% |
| Security best practices | 15% |

---

## 📊 Evaluation

| Grade | Score |
|-------|-------|
| Excellent | 90-100% |
| Good | 75-89% |
| Pass | 60-74% |
| Fail | < 60% |

---

## 🚀 Getting Started

1. Setup Kubernetes cluster (minikube/kind)
2. Deploy base infrastructure
3. Build and deploy applications
4. Setup CI/CD
5. Configure monitoring
6. Document everything

---

**Good luck! 🚀**

---

**[← Back to Track 2](../README.md)** | **[Next: Track 3 →](../../Track3_Cloud_Network_Design/)**
