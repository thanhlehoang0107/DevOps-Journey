# 🔧 Troubleshooting - Xử lý lỗi phổ biến

> Các giải pháp cho lỗi thường gặp khi cài đặt môi trường

---

## 📋 Mục lục

1. [Docker Issues](#-docker-issues)
2. [WSL2 Issues (Windows)](#-wsl2-issues-windows)
3. [Git Issues](#-git-issues)
4. [Kubernetes Issues](#-kubernetes-issues)
5. [Network Issues](#-network-issues)

---

## 🐳 Docker Issues

### Docker daemon không chạy

**Lỗi:**

```
Cannot connect to the Docker daemon at unix:///var/run/docker.sock
```

**Giải pháp:**

```bash
# Linux
sudo systemctl start docker
sudo systemctl enable docker

# Windows - Mở Docker Desktop từ Start Menu
# macOS - Mở Docker Desktop từ Applications
```

---

### Permission denied khi chạy docker

**Lỗi:**

```
Got permission denied while trying to connect to the Docker daemon socket
```

**Giải pháp (Linux):**

```bash
# Thêm user vào group docker
sudo usermod -aG docker $USER

# Logout và login lại, hoặc:
newgrp docker
```

---

### Docker build chậm hoặc timeout

**Giải pháp:**

```bash
# Xóa cache và images không dùng
docker system prune -a

# Tăng resources cho Docker Desktop:
# Settings → Resources → Increase Memory/CPU
```

---

### Port đã được sử dụng

**Lỗi:**

```
Bind for 0.0.0.0:80: failed: port is already allocated
```

**Giải pháp:**

```bash
# Tìm process đang dùng port
# Windows
netstat -ano | findstr :80

# Linux/macOS
lsof -i :80

# Kill process hoặc dùng port khác
docker run -p 8080:80 nginx
```

---

## 🪟 WSL2 Issues (Windows)

### WSL2 chưa được cài đặt

**Lỗi:**

```
WSL 2 requires an update to its kernel component
```

**Giải pháp:**

```powershell
# Chạy PowerShell (Admin)
wsl --install
wsl --update

# Restart máy tính
```

---

### WSL2 không start được

**Giải pháp:**

```powershell
# Kiểm tra virtualization đã bật chưa (BIOS)
# Bật Windows features:
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

# Restart
```

---

### Docker integration với WSL2 không hoạt động

**Giải pháp:**

1. Mở Docker Desktop
2. Settings → Resources → WSL Integration
3. Tick "Enable integration with my default WSL distro"
4. Tick distro bạn đang dùng (Ubuntu, etc.)
5. Apply & Restart

---

## 📦 Git Issues

### Git không nhận SSH key

**Lỗi:**

```
Permission denied (publickey)
```

**Giải pháp:**

```bash
# Tạo SSH key mới
ssh-keygen -t ed25519 -C "your_email@example.com"

# Start SSH agent
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

# Copy public key và add vào GitHub
cat ~/.ssh/id_ed25519.pub
# Paste vào GitHub → Settings → SSH Keys
```

---

### Git push bị từ chối

**Lỗi:**

```
error: failed to push some refs
hint: Updates were rejected because the remote contains work that you do not have locally
```

**Giải pháp:**

```bash
# Pull changes trước
git pull origin main --rebase

# Rồi push lại
git push origin main
```

---

### Line ending issues (CRLF/LF)

**Giải pháp:**

```bash
# Windows - tự động convert
git config --global core.autocrlf true

# Linux/macOS
git config --global core.autocrlf input
```

---

## ☸️ Kubernetes Issues

### kubectl không connect được cluster

**Lỗi:**

```
The connection to the server localhost:8080 was refused
```

**Giải pháp:**

```bash
# Kiểm tra minikube đang chạy
minikube status

# Start nếu chưa chạy
minikube start

# Set kubectl context
kubectl config use-context minikube
```

---

### Minikube start thất bại

**Giải pháp:**

```bash
# Xóa cluster cũ và tạo mới
minikube delete
minikube start --driver=docker

# Nếu vẫn lỗi, thử driver khác
minikube start --driver=virtualbox
```

---

### Pod stuck ở Pending

**Kiểm tra:**

```bash
kubectl describe pod <pod-name>
kubectl get events
```

**Nguyên nhân phổ biến:**

- Không đủ resources → Tăng minikube resources
- ImagePullBackOff → Kiểm tra image name, registry credentials

---

## 🌐 Network Issues

### Không thể pull Docker images

**Lỗi:**

```
Error response from daemon: Get https://registry-1.docker.io/v2/: net/http: request canceled
```

**Giải pháp:**

```bash
# Kiểm tra DNS
nslookup registry-1.docker.io

# Thử dùng mirror (add vào Docker daemon.json)
{
  "registry-mirrors": ["https://mirror.gcr.io"]
}

# Hoặc dùng VPN nếu registry bị block
```

---

### Proxy issues

**Giải pháp:**

```bash
# Set proxy cho Docker
# Windows: Docker Desktop → Settings → Resources → Proxies

# Linux: Thêm vào /etc/systemd/system/docker.service.d/http-proxy.conf
[Service]
Environment="HTTP_PROXY=http://proxy.example.com:8080"
Environment="HTTPS_PROXY=http://proxy.example.com:8080"

# Reload
sudo systemctl daemon-reload
sudo systemctl restart docker
```

---

## 💡 Tips chung

### Kiểm tra logs

```bash
# Docker container logs
docker logs <container_id>

# Docker system logs (Linux)
journalctl -u docker.service

# Kubernetes pod logs
kubectl logs <pod-name>
```

### Reset môi trường hoàn toàn

```bash
# Docker - xóa tất cả
docker system prune -a --volumes

# Minikube - xóa cluster
minikube delete --all

# Git - reset repo
git clean -fdx
git reset --hard HEAD
```

---

## 🆘 Vẫn không giải quyết được?

1. **Google error message** - Copy chính xác error và search
2. **Stack Overflow** - Tìm với tag [docker], [kubernetes], etc.
3. **GitHub Issues** - Tìm trong repo của tool
4. **Hỏi trong community** - Discord/Slack của các dự án

---

## 🔗 Navigation

[⬅️ Tools Overview](./TOOLS_OVERVIEW.md) | [README](./README.md) | [Cheatsheet ➡️](./CHEATSHEET.md)

---

*Cập nhật: 2025-12-29*
