# 🛠️ Tools Overview - Tổng Quan Công Cụ DevOps

> Hướng dẫn tổng quan tất cả tools cần thiết cho từng Track

---

## 📋 Mục lục

1. [Bảng tổng hợp Tools](#bảng-tổng-hợp-tools)
2. [Track 1: Foundation & Static Web](#-track-1-foundation--static-web)
3. [Track 2: Orchestration & Automation](#-track-2-orchestration--automation)
4. [Track 3: Cloud, Network & Design](#-track-3-cloud-network--design)
5. [Track 4: DevSecOps](#-track-4-devsecops)

---

## Bảng tổng hợp Tools

| Tool | Track 1 | Track 2 | Track 3 | Track 4 | Mô tả |
|------|:-------:|:-------:|:-------:|:-------:|-------|
| WSL2 (Windows) | ✅ | - | - | - | Linux subsystem cho Windows |
| Homebrew (macOS) | ✅ | - | - | - | Package manager cho macOS |
| Git | ✅ | - | - | - | Version control |
| VS Code | ✅ | - | - | - | Code editor |
| Docker | ✅ | - | - | - | Container runtime |
| Docker Compose | ✅ | - | - | - | Multi-container orchestration |
| NGINX | ✅ | - | - | - | Web server |
| Node.js | ✅ | - | - | - | JavaScript runtime (optional) |
| kubectl | - | ✅ | - | - | Kubernetes CLI |
| Minikube/Kind | - | ✅ | - | - | Local Kubernetes |
| Helm | - | ✅ | - | - | K8s package manager |
| Jenkins | - | ✅ | - | - | CI/CD server |
| Terraform | - | - | ✅ | - | Infrastructure as Code |
| AWS CLI | - | - | ✅ | - | AWS command line |
| Ansible | - | - | ✅ | - | Configuration management |
| Trivy | - | - | - | ✅ | Container vulnerability scanner |
| Hadolint | - | - | - | ✅ | Dockerfile linter |
| OWASP ZAP | - | - | - | ✅ | Web app security scanner |

---

## 🔵 Track 1: Foundation & Static Web

### Danh sách Tools

| # | Tool | Version | Lệnh kiểm tra | Output mong đợi |
|---|------|---------|---------------|-----------------|
| 1 | WSL2 (Windows) | 2.x | `wsl --version` | `WSL version: 2.x.x` |
| 2 | Git | 2.40+ | `git --version` | `git version 2.4x.x` |
| 3 | VS Code | Latest | `code --version` | `1.8x.x` |
| 4 | Docker | 24.0+ | `docker --version` | `Docker version 24.x.x` |
| 5 | Docker Compose | 2.20+ | `docker compose version` | `v2.2x.x` |
| 6 | NGINX | Latest | `docker run --rm nginx:alpine nginx -v` | `nginx/1.2x.x` |

### Chi tiết từng Tool

#### 1. Git

- **Là gì**: Hệ thống quản lý phiên bản phân tán (DVCS)
- **Tại sao học**: Mọi dự án DevOps đều sử dụng Git để quản lý code
- **Website**: <https://git-scm.com/>
- **Cài đặt nhanh**:

  ```bash
  # Windows (PowerShell Admin)
  winget install Git.Git
  
  # macOS
  brew install git
  
  # Linux (Ubuntu/Debian)
  sudo apt install git
  ```

#### 2. VS Code

- **Là gì**: Code editor nhẹ nhưng mạnh mẽ của Microsoft
- **Tại sao học**: Extensions tuyệt vời cho DevOps (Docker, K8s, Terraform)
- **Website**: <https://code.visualstudio.com/>
- **Extensions khuyến nghị**:
  - Docker
  - Remote - SSH
  - YAML
  - GitLens

#### 3. Docker

- **Là gì**: Platform containerization hàng đầu
- **Tại sao học**: Container là nền tảng của DevOps hiện đại
- **Website**: <https://www.docker.com/>
- **Kiểm tra cài đặt**:

  ```bash
  docker run hello-world
  ```

#### 4. NGINX

- **Là gì**: Web server/reverse proxy hiệu suất cao
- **Tại sao học**: Serve static files, reverse proxy cho microservices
- **Website**: <https://nginx.org/>
- **Chạy nhanh với Docker**:

  ```bash
  docker run -d -p 80:80 nginx:alpine
  ```

---

## 🟢 Track 2: Orchestration & Automation

### Danh sách Tools bổ sung

| # | Tool | Version | Lệnh kiểm tra | Output mong đợi |
|---|------|---------|---------------|-----------------|
| 1 | kubectl | 1.28+ | `kubectl version --client` | `v1.2x.x` |
| 2 | Minikube | 1.31+ | `minikube version` | `v1.3x.x` |
| 3 | Helm | 3.12+ | `helm version` | `v3.1x.x` |
| 4 | Jenkins | LTS | Docker container | - |

### Chi tiết từng Tool

#### 1. kubectl

- **Là gì**: CLI chính thức để tương tác với Kubernetes
- **Tại sao học**: Quản lý và debug K8s clusters
- **Website**: <https://kubernetes.io/docs/tasks/tools/>
- **Cài đặt**:

  ```bash
  # Windows
  winget install Kubernetes.kubectl
  
  # macOS
  brew install kubectl
  
  # Linux
  curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
  ```

#### 2. Minikube

- **Là gì**: Chạy Kubernetes single-node trên local
- **Tại sao học**: Học K8s mà không cần cloud account
- **Website**: <https://minikube.sigs.k8s.io/>
- **Khởi động**:

  ```bash
  minikube start --driver=docker
  ```

#### 3. Helm

- **Là gì**: Package manager cho Kubernetes
- **Tại sao học**: Cài đặt ứng dụng phức tạp chỉ với 1 lệnh
- **Website**: <https://helm.sh/>
- **Ví dụ**:

  ```bash
  helm repo add bitnami https://charts.bitnami.com/bitnami
  helm install my-nginx bitnami/nginx
  ```

#### 4. Jenkins

- **Là gì**: CI/CD server mã nguồn mở phổ biến nhất
- **Tại sao học**: Tự động hóa build, test, deploy
- **Website**: <https://www.jenkins.io/>
- **Chạy với Docker**:

  ```bash
  docker run -d -p 8080:8080 jenkins/jenkins:lts
  ```

---

## 🟡 Track 3: Cloud, Network & Design

### Danh sách Tools bổ sung

| # | Tool | Version | Lệnh kiểm tra | Output mong đợi |
|---|------|---------|---------------|-----------------|
| 1 | Terraform | 1.5+ | `terraform --version` | `v1.x.x` |
| 2 | AWS CLI | 2.x | `aws --version` | `aws-cli/2.x.x` |
| 3 | Ansible | 2.14+ | `ansible --version` | `ansible 2.1x.x` |

### Chi tiết từng Tool

#### 1. Terraform

- **Là gì**: Infrastructure as Code tool của HashiCorp
- **Tại sao học**: Quản lý infrastructure trên mọi cloud provider
- **Website**: <https://www.terraform.io/>
- **Workflow cơ bản**:

  ```bash
  terraform init    # Khởi tạo
  terraform plan    # Xem preview
  terraform apply   # Áp dụng changes
  terraform destroy # Xóa resources
  ```

#### 2. AWS CLI

- **Là gì**: Command line interface cho Amazon Web Services
- **Tại sao học**: Tự động hóa AWS operations
- **Website**: <https://aws.amazon.com/cli/>
- **Cấu hình**:

  ```bash
  aws configure
  # Nhập: Access Key, Secret Key, Region, Output format
  ```

#### 3. Ansible

- **Là gì**: Configuration management và automation tool
- **Tại sao học**: Quản lý cấu hình server ở scale lớn
- **Website**: <https://www.ansible.com/>

---

## 🔴 Track 4: DevSecOps

### Danh sách Tools bổ sung

| # | Tool | Version | Lệnh kiểm tra | Output mong đợi |
|---|------|---------|---------------|-----------------|
| 1 | Trivy | Latest | `trivy --version` | `Version: 0.x.x` |
| 2 | Hadolint | Latest | `hadolint --version` | `Haskell Dockerfile Linter` |
| 3 | OWASP ZAP | Latest | Docker container | - |

### Chi tiết từng Tool

#### 1. Trivy

- **Là gì**: Vulnerability scanner cho containers và IaC
- **Tại sao học**: Tìm CVE trong Docker images
- **Website**: <https://trivy.dev/>
- **Scan image**:

  ```bash
  trivy image nginx:latest
  ```

#### 2. Hadolint

- **Là gì**: Dockerfile linter theo best practices
- **Tại sao học**: Viết Dockerfile an toàn và tối ưu
- **Website**: <https://github.com/hadolint/hadolint>
- **Sử dụng**:

  ```bash
  hadolint Dockerfile
  ```

#### 3. OWASP ZAP

- **Là gì**: Web application security scanner
- **Tại sao học**: Tìm lỗ hổng bảo mật trong web apps
- **Website**: <https://www.zaproxy.org/>

---

## 💡 Tips

### Thứ tự cài đặt khuyến nghị

```
Track 1: Git → VS Code → Docker → Verify
    ↓
Track 2: kubectl → Minikube → Helm → Jenkins → Verify
    ↓
Track 3: Terraform → AWS CLI → Ansible → Verify
    ↓
Track 4: Trivy → Hadolint → OWASP ZAP → Verify
```

### Lưu ý quan trọng

1. **Cài đặt theo track** - Không cần cài tất cả tools từ đầu
2. **Verify sau mỗi cài đặt** - Chạy script verify để đảm bảo tools hoạt động
3. **Docker-first** - Nhiều tools có thể chạy trong Docker container thay vì cài local

---

## 🔗 Navigation

[⬅️ README](./README.md) | [Windows Setup](./WINDOWS_SETUP.md) | [Troubleshooting ➡️](./TROUBLESHOOTING.md)

---

*Cập nhật: 2025-12-29*
