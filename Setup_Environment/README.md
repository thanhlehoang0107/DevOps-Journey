# 🛠️ Setup Environment

> **Hướng dẫn cài đặt môi trường phát triển** cho DevOps Journey.

---

## 📋 Mục Lục

- [Yêu Cầu Hệ Thống](#-yêu-cầu-hệ-thống)
- [Cài Đặt Theo OS](#-cài-đặt-theo-os)
- [Tools Overview](#-tools-overview)
- [Verification](#-verification)
- [Troubleshooting](#-troubleshooting)

---

## 💻 Yêu Cầu Hệ Thống

### Hardware Requirements

| Component | Minimum | Recommended |
|-----------|---------|-------------|
| **RAM** | 8 GB | 16 GB |
| **Storage** | 50 GB SSD | 100 GB SSD |
| **CPU** | 4 cores | 8 cores |
| **Network** | Stable internet | Stable internet |

### Supported Operating Systems

- ✅ **Windows 10/11** (với WSL2)
- ✅ **macOS** (Monterey trở lên)
- ✅ **Linux** (Ubuntu 20.04+, Fedora 35+)

---

## 🔧 Cài Đặt Theo OS

### Windows 10/11

#### 1. Cài đặt WSL2 (Windows Subsystem for Linux)

```powershell
# Mở PowerShell as Administrator
wsl --install

# Restart máy tính
# Sau khi restart, Ubuntu sẽ được cài đặt tự động
```

#### 2. Cài đặt Windows Terminal

```powershell
# Từ Microsoft Store hoặc
winget install Microsoft.WindowsTerminal
```

#### 3. Cài đặt Docker Desktop

1. Download từ [docker.com](https://www.docker.com/products/docker-desktop/)
2. Chạy installer
3. Enable WSL2 backend trong settings
4. Restart Docker Desktop

#### 4. Cài đặt Git

```powershell
winget install Git.Git
```

#### 5. Cài đặt VS Code

```powershell
winget install Microsoft.VisualStudioCode
```

#### 6. Cài đặt Python

```powershell
winget install Python.Python.3.12
```

---

### macOS

#### 1. Cài đặt Homebrew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

#### 2. Cài đặt các tools

```bash
# Git
brew install git

# Docker Desktop
brew install --cask docker

# VS Code
brew install --cask visual-studio-code

# Python
brew install python@3.12

# iTerm2 (optional nhưng recommended)
brew install --cask iterm2
```

---

### Linux (Ubuntu/Debian)

#### 1. Update system

```bash
sudo apt update && sudo apt upgrade -y
```

#### 2. Cài đặt Git

```bash
sudo apt install git -y
```

#### 3. Cài đặt Docker

```bash
# Add Docker's GPG key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# Add repository
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Install Docker
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y

# Add user to docker group
sudo usermod -aG docker $USER
newgrp docker
```

#### 4. Cài đặt Python

```bash
sudo apt install python3 python3-pip python3-venv -y
```

#### 5. Cài đặt VS Code

```bash
sudo snap install code --classic
```

---

## 📦 Tools Overview

Chi tiết về các tools được sử dụng trong course → **[TOOLS_OVERVIEW.md](./TOOLS_OVERVIEW.md)**

| Track | Tools |
|-------|-------|
| **Track 1** | Linux, Bash, Python, Git, Docker, NGINX, GitHub Actions |
| **Track 2** | Docker Compose, Jenkins, Kubernetes, Prometheus, Grafana |
| **Track 3** | AWS CLI, Terraform, Ansible, MySQL, PostgreSQL, Redis |
| **Track 4** | Trivy, SonarQube, HashiCorp Vault, OWASP ZAP |
| **Track 5** | N/A (Career focused) |

---

## ✅ Verification

Chạy các lệnh sau để verify cài đặt:

```bash
# Git
git --version
# Expected: git version 2.x.x

# Docker
docker --version
# Expected: Docker version 24.x.x

docker compose version
# Expected: Docker Compose version v2.x.x

# Python
python3 --version
# Expected: Python 3.x.x

# VS Code
code --version
# Expected: 1.x.x
```

### Quick Test

```bash
# Test Docker
docker run hello-world

# Test Git
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
git config --list

# Test Python
python3 -c "print('Hello DevOps!')"
```

---

## 🔧 VS Code Extensions

### Recommended Extensions

```bash
# Install via command line
code --install-extension ms-vscode-remote.remote-wsl
code --install-extension ms-azuretools.vscode-docker
code --install-extension ms-python.python
code --install-extension hashicorp.terraform
code --install-extension redhat.ansible
code --install-extension ms-kubernetes-tools.vscode-kubernetes-tools
code --install-extension github.vscode-github-actions
code --install-extension eamodio.gitlens
```

### Extension List

| Extension | Mục Đích |
|-----------|----------|
| Remote - WSL | Làm việc với WSL trong VS Code |
| Docker | Docker support |
| Python | Python language support |
| Terraform | Terraform syntax & validation |
| Ansible | Ansible playbook support |
| Kubernetes | K8s cluster management |
| GitHub Actions | Workflow editing |
| GitLens | Advanced Git features |

---

## 🔧 Git Configuration

### Basic Configuration

```bash
# Thông tin user
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Default branch
git config --global init.defaultBranch main

# Editor
git config --global core.editor "code --wait"

# Pull strategy
git config --global pull.rebase false
```

### SSH Setup for GitHub

```bash
# Generate SSH key
ssh-keygen -t ed25519 -C "your.email@example.com"

# Start ssh-agent
eval "$(ssh-agent -s)"

# Add key
ssh-add ~/.ssh/id_ed25519

# Copy public key
cat ~/.ssh/id_ed25519.pub
# Paste this key to GitHub Settings > SSH Keys

# Test connection
ssh -T git@github.com
```

---

## ❓ Troubleshooting

Xem hướng dẫn xử lý lỗi chi tiết → **[TROUBLESHOOTING.md](./TROUBLESHOOTING.md)**

### Common Issues

| Issue | Solution |
|-------|----------|
| Docker daemon not running | Restart Docker Desktop |
| WSL2 not working | `wsl --update` |
| Permission denied (Docker) | `sudo usermod -aG docker $USER` |
| Git authentication failed | Setup SSH key |

---

## 📋 Cheatsheet

Xem tất cả commands quan trọng → **[CHEATSHEET.md](./CHEATSHEET.md)**

---

## 🔗 Navigation

| ← Previous | Current | Next → |
|------------|---------|--------|
| [Main README](../README.md) | **Setup Environment** | [Track 1: Foundation](../Track1_Foundation_StaticWeb/) |

---

<div align="center">

**Sau khi cài đặt xong, hãy bắt đầu với [Track 1 →](../Track1_Foundation_StaticWeb/)**

</div>
