# 📋 Cheatsheet - Tra cứu nhanh

> Tất cả lệnh quan trọng trên một trang

---

## 🔍 Verify Installation

### Quick Check - Tất cả tools

```bash
# Track 1
git --version
docker --version
docker compose version
code --version

# Track 2
kubectl version --client
minikube version
helm version

# Track 3
terraform --version
aws --version
ansible --version

# Track 4
trivy --version
hadolint --version
```

---

## 🐳 Docker Commands

### Images

```bash
docker images                    # Liệt kê images
docker pull nginx:alpine         # Download image
docker build -t myapp .          # Build image từ Dockerfile
docker rmi image_name            # Xóa image
docker image prune               # Xóa images không dùng
```

### Containers

```bash
docker ps                        # Containers đang chạy
docker ps -a                     # Tất cả containers
docker run -d -p 80:80 nginx     # Chạy container
docker stop container_id         # Dừng container
docker rm container_id           # Xóa container
docker exec -it container bash   # Vào terminal container
docker logs container_id         # Xem logs
```

### Docker Compose

```bash
docker compose up -d             # Khởi động services
docker compose down              # Dừng và xóa containers
docker compose logs -f           # Follow logs
docker compose ps                # Liệt kê services
docker compose build             # Build lại images
```

### Cleanup

```bash
docker system prune              # Xóa resources không dùng
docker system prune -a           # Xóa tất cả images không dùng
docker volume prune              # Xóa volumes không dùng
```

---

## 📦 Git Commands

### Cơ bản

```bash
git init                         # Khởi tạo repo
git clone <url>                  # Clone repo
git status                       # Xem trạng thái
git add .                        # Stage tất cả
git commit -m "message"          # Commit
git push origin main             # Push lên remote
git pull origin main             # Pull từ remote
```

### Branches

```bash
git branch                       # Liệt kê branches
git branch feature-x             # Tạo branch mới
git checkout feature-x           # Chuyển branch
git checkout -b feature-x        # Tạo và chuyển branch
git merge feature-x              # Merge branch
git branch -d feature-x          # Xóa branch
```

### Undo

```bash
git restore file.txt             # Hoàn tác thay đổi file
git restore --staged file.txt    # Unstage file
git reset --soft HEAD~1          # Undo commit giữ changes
git reset --hard HEAD~1          # Undo commit xóa changes
```

---

## ☸️ Kubernetes Commands

### Cluster

```bash
minikube start                   # Khởi động cluster
minikube stop                    # Dừng cluster
minikube delete                  # Xóa cluster
minikube dashboard               # Mở dashboard
```

### kubectl Basics

```bash
kubectl get pods                 # Liệt kê pods
kubectl get services             # Liệt kê services
kubectl get deployments          # Liệt kê deployments
kubectl get all                  # Liệt kê tất cả resources
kubectl get all -A               # Tất cả namespaces
```

### kubectl Operations

```bash
kubectl apply -f file.yaml       # Áp dụng manifest
kubectl delete -f file.yaml      # Xóa resources
kubectl describe pod pod-name    # Chi tiết pod
kubectl logs pod-name            # Xem logs
kubectl exec -it pod-name -- sh  # Vào shell của pod
kubectl port-forward pod 8080:80 # Forward port
```

### Helm

```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update                 # Update repos
helm search repo nginx           # Tìm charts
helm install my-app bitnami/nginx  # Cài đặt chart
helm list                        # Liệt kê releases
helm uninstall my-app            # Gỡ cài đặt
```

---

## 🏗️ Terraform Commands

```bash
terraform init                   # Khởi tạo
terraform fmt                    # Format code
terraform validate               # Validate syntax
terraform plan                   # Preview changes
terraform apply                  # Áp dụng changes
terraform apply -auto-approve    # Áp dụng không hỏi
terraform destroy                # Xóa tất cả resources
terraform state list             # Liệt kê state
terraform output                 # Xem outputs
```

---

## ☁️ AWS CLI Commands

### Configuration

```bash
aws configure                    # Cấu hình credentials
aws sts get-caller-identity      # Kiểm tra identity
```

### EC2

```bash
aws ec2 describe-instances       # Liệt kê instances
aws ec2 start-instances --instance-ids i-xxx
aws ec2 stop-instances --instance-ids i-xxx
```

### S3

```bash
aws s3 ls                        # Liệt kê buckets
aws s3 ls s3://bucket-name       # Liệt kê objects
aws s3 cp file.txt s3://bucket/  # Upload file
aws s3 sync ./folder s3://bucket/ # Sync folder
```

---

## 🔒 Security Tools

### Trivy

```bash
trivy image nginx:latest         # Scan image
trivy image --severity HIGH,CRITICAL nginx
trivy fs .                       # Scan filesystem
trivy config .                   # Scan IaC files
```

### Hadolint

```bash
hadolint Dockerfile              # Lint Dockerfile
hadolint --ignore DL3008 Dockerfile  # Ignore rule
```

---

## 🔧 Useful Shortcuts

### VS Code Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+Shift+P` | Command Palette |
| `Ctrl+`` ` | Toggle Terminal |
| `Ctrl+B` | Toggle Sidebar |
| `Ctrl+Shift+E` | Explorer |
| `Ctrl+Shift+G` | Git |
| `Ctrl+Shift+F` | Search in files |

### Terminal Shortcuts (Bash)

| Shortcut | Action |
|----------|--------|
| `Ctrl+C` | Cancel command |
| `Ctrl+L` | Clear screen |
| `Ctrl+R` | Search history |
| `Tab` | Auto-complete |
| `!!` | Run last command |
| `!$` | Last argument of previous command |

---

## 🔗 Quick Links

- Docker Hub: <https://hub.docker.com/>
- Kubernetes Docs: <https://kubernetes.io/docs/>
- Terraform Registry: <https://registry.terraform.io/>
- AWS Console: <https://console.aws.amazon.com/>

---

## 🔗 Navigation

[⬅️ Troubleshooting](./TROUBLESHOOTING.md) | [README](./README.md) | [Quiz ➡️](./QUIZ.md)

---

*Cập nhật: 2025-12-29*
