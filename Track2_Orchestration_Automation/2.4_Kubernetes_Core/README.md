# ☸️ Module 2.4: Kubernetes Core

[![Duration](https://img.shields.io/badge/Duration-1--2%20weeks-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Intermediate-orange?style=flat-square)](.)

> **Container Orchestration** - Deploy and manage containers with Kubernetes.
>
> *Điều phối Container - Deploy và quản lý containers với Kubernetes.*

---

## 🎯 Learning Objectives (Mục tiêu học tập)

After this module, you will (Sau module này, bạn sẽ):

- ✅ Understand Kubernetes architecture (Hiểu kiến trúc Kubernetes)
- ✅ Deploy applications with kubectl (Deploy ứng dụng với kubectl)
- ✅ Work with Pods, Deployments, Services (Làm việc với Pods, Deployments, Services)
- ✅ Use ConfigMaps and Secrets (Sử dụng ConfigMaps và Secrets)
- ✅ Implement Persistent storage (Triển khai lưu trữ bền vững)
- ✅ Perform Rolling updates and rollbacks (Thực hiện cập nhật và hoàn tác)

---

## 📚 Content (Nội dung)

### 1. Architecture (Kiến trúc)

```
┌─────────────────────────────────────────┐
│              Control Plane               │
│  ┌─────────┐ ┌─────────┐ ┌───────────┐  │
│  │ API     │ │ etcd    │ │ Scheduler │  │
│  │ Server  │ │         │ │           │  │
│  └─────────┘ └─────────┘ └───────────┘  │
│  ┌─────────────────────────────────────┐│
│  │     Controller Manager              ││
│  └─────────────────────────────────────┘│
└─────────────────────────────────────────┘
            │
┌───────────┼───────────────────────────┐
│           │      Worker Nodes          │
│  ┌────────┴────────┐  ┌──────────────┐│
│  │     kubelet     │  │ kube-proxy   ││
│  └─────────────────┘  └──────────────┘│
│  ┌─────────────────────────────────────┐
│  │            Pods                     ││
│  └─────────────────────────────────────┘
└───────────────────────────────────────┘
```

### 2. Basic Resources (Tài nguyên cơ bản)

```yaml
# Pod
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
    - name: nginx
      image: nginx:alpine
      ports:
        - containerPort: 80

---
# Deployment
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx:alpine
          ports:
            - containerPort: 80

---
# Service
apiVersion: v1
kind: Service
metadata:
  name: nginx
spec:
  selector:
    app: nginx
  ports:
    - port: 80
      targetPort: 80
  type: ClusterIP
```

### 3. kubectl Commands (Các lệnh kubectl)

```bash
# Cluster info (Thông tin cluster)
kubectl cluster-info
kubectl get nodes

# Pods
kubectl get pods
kubectl describe pod <name>
kubectl logs <pod>
kubectl exec -it <pod> -- sh

# Deployments
kubectl create deployment nginx --image=nginx
kubectl scale deployment nginx --replicas=3
kubectl set image deployment/nginx nginx=nginx:1.20

# Services
kubectl expose deployment nginx --port=80 --type=LoadBalancer
kubectl get services

# Apply manifests (Áp dụng manifests)
kubectl apply -f manifest.yaml
kubectl delete -f manifest.yaml
```

### 4. ConfigMaps & Secrets

```yaml
# ConfigMap
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
data:
  APP_ENV: production
  LOG_LEVEL: info

---
# Secret
apiVersion: v1
kind: Secret
metadata:
  name: app-secret
type: Opaque
data:
  DB_PASSWORD: cGFzc3dvcmQ=  # base64 encoded (mã hóa base64)
```

### 5. Persistent Volume (Volume bền vững)

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: data-pvc
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi

---
# Use in Pod (Sử dụng trong Pod)
spec:
  volumes:
    - name: data
      persistentVolumeClaim:
        claimName: data-pvc
  containers:
    - name: app
      volumeMounts:
        - mountPath: /data
          name: data
```

---

## 📝 Module Files (Các file trong Module)

| File | Description (Mô tả) |
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

| ← Previous (Trước) | Current (Hiện tại) | Next (Tiếp) → |
|:------------------:|:------------------:|:-------------:|
| [2.3 Jenkins](../2.3_Jenkins/) | **2.4 Kubernetes Core** | [2.5 Monitoring](../2.5_Monitoring_Logging/) |

---

**Master container orchestration with Kubernetes! ☸️**

*Thành thạo điều phối container với Kubernetes!*

</div>
