# ☸️ Module 2.4: Kubernetes Core

[![Duration](https://img.shields.io/badge/Duration-1--2%20weeks-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Intermediate-orange?style=flat-square)](.)

> **Container Orchestration** - Deploy và manage containers với Kubernetes.

---

## 🎯 Learning Objectives

- ✅ Hiểu Kubernetes architecture
- ✅ Deploy applications với kubectl
- ✅ Work với Pods, Deployments, Services
- ✅ ConfigMaps và Secrets
- ✅ Persistent storage
- ✅ Rolling updates và rollbacks

---

## 📚 Content

### 1. Architecture

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

### 2. Basic Resources

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

### 3. kubectl Commands

```bash
# Cluster info
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

# Apply manifests
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
  DB_PASSWORD: cGFzc3dvcmQ=  # base64 encoded
```

### 5. Persistent Volume

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
# Use in Pod
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

## 📝 Module Files

| File | Description |
|------|-------------|
| [LABS.md](./LABS.md) | Hands-on labs |
| [QUIZ.md](./QUIZ.md) | Knowledge check |
| [EXERCISES.md](./EXERCISES.md) | Exercises |
| [PROJECT.md](./PROJECT.md) | Mini project |
| [SOLUTIONS.md](./SOLUTIONS.md) | Solutions |
| [CHEATSHEET.md](./CHEATSHEET.md) | Quick reference |
