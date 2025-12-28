# 🔧 Software Links – Tài liệu cài đặt công cụ

---

## Giới thiệu

Tài liệu này tổng hợp link tải chính thức và hướng dẫn cài đặt các công cụ cần thiết cho khóa học DevOps.

> ⚠️ **Lưu ý:** Chỉ tải từ nguồn chính thức để đảm bảo an toàn.

---

## 1. Môi trường cơ bản

### 1.1 Windows Subsystem for Linux (WSL2)

| Thông tin | Link |
|-----------|------|
| *Tài liệu* | [Microsoft Docs](https://learn.microsoft.com/en-us/windows/wsl/install) |
| *Yêu cầu* | Windows 10 version 2004+ hoặc Windows 11 |

**Windows**

| Thông tin | GUI Installation | CLI Installation |
|-----------|------------------|------------------|
| *Install* | [Download](https://www.docker.com/products/docker-desktop/) | `choco install docker-desktop` |
| *Uninstall* | - | `choco uninstall docker-desktop` |

**macOS**

| Thông tin | GUI Installation | CLI Installation |
|-----------|------------------|------------------|
| *Install* |  |  |
| *Uninstall* |  |  |

**Linux**

| Thông tin | GUI Installation | CLI Installation |
|-----------|------------------|------------------|
| *Install* |  |  |
| *Uninstall* |  |  |

**Verify:**

    ```bash

    ```
---

### 1.2 Docker Desktop

| Thông tin | Link |
|-----------|------|
| *Tài liệu* | [Docker Docs](https://docs.docker.com/desktop/install/) |

**Windows**

| Thông tin | GUI Installation | CLI Installation |
|-----------|------------------|------------------|
| *Install* | [Download](https://www.docker.com/products/docker-desktop/) | `choco install docker-desktop` |
| *Uninstall* | - | `choco uninstall docker-desktop` |

**macOS**

| Thông tin | GUI Installation | CLI Installation |
|-----------|------------------|------------------|
| *Install* |  |  |
| *Uninstall* |  |  |

**Linux**

| Thông tin | GUI Installation | CLI Installation |
|-----------|------------------|------------------|
| *Install* |  |  |
| *Uninstall* |  |  |

**Verify:**

    ```bash

    ```
---

### 1.3 Git

| Thông tin | Link |
|-----------|------|
| *Tài liệu* |  |

**Windows**

| Thông tin | GUI Installation | CLI Installation |
|-----------|------------------|------------------|
| *Install* |  |  |
| *Uninstall* |  |  |

**macOS**

| Thông tin | GUI Installation | CLI Installation |
|-----------|------------------|------------------|
| *Install* |  |  |
| *Uninstall* |  |  |

**Linux**

| Thông tin | GUI Installation | CLI Installation |
|-----------|------------------|------------------|
| *Install* |  |  |
| *Uninstall* |  |  |

**Verify:**

    ```bash

    ```
---

## 2. Code Editor

### 2.1 Visual Studio Code

| Thông tin | Link |
|-----------|------|
| *Tài liệu* |  |

**Windows**

| Thông tin | GUI Installation | CLI Installation |
|-----------|------------------|------------------|
| *Install* |  |  |
| *Uninstall* |  |  |

**macOS**

| Thông tin | GUI Installation | CLI Installation |
|-----------|------------------|------------------|
| *Install* |  |  |
| *Uninstall* |  |  |

**Linux**

| Thông tin | GUI Installation | CLI Installation |
|-----------|------------------|------------------|
| *Install* |  |  |
| *Uninstall* |  |  |

**Verify:**

    ```bash

    ```

### 2.2 Extensions khuyến nghị

- Docker
- Remote - WSL
- Remote - SSH
- GitLens
- YAML
- Markdown All in One
- Mermaid Markdown Syntax Highlighting

---

## 3. Container & Orchestration

### 3.1 kubectl (Kubernetes CLI)

| Thông tin | Link |
|-----------|------|
| *Tài liệu* |  |

**Windows**

| Thông tin | GUI Installation | CLI Installation |
|-----------|------------------|------------------|
| *Install* |  |  |
| *Uninstall* |  |  |

**macOS**

| Thông tin | GUI Installation | CLI Installation |
|-----------|------------------|------------------|
| *Install* |  |  |
| *Uninstall* |  |  |

**Linux**

| Thông tin | GUI Installation | CLI Installation |
|-----------|------------------|------------------|
| *Install* |  |  |
| *Uninstall* |  |  |

**Verify:**

    ```bash

    ```
---

### 3.2 Minikube (Local Kubernetes)

| Thông tin | Link |
|-----------|------|
| *Tài liệu* |  |

**Windows**

| Thông tin | GUI Installation | CLI Installation |
|-----------|------------------|------------------|
| *Install* |  |  |
| *Uninstall* |  |  |

**macOS**

| Thông tin | GUI Installation | CLI Installation |
|-----------|------------------|------------------|
| *Install* |  |  |
| *Uninstall* |  |  |

**Linux**

| Thông tin | GUI Installation | CLI Installation |
|-----------|------------------|------------------|
| *Install* |  |  |
| *Uninstall* |  |  |

**Verify:**

    ```bash

    ```
---

### 3.3 Helm (Kubernetes Package Manager)

| Thông tin | Link |
|-----------|------|
| *Tài liệu* |  |

**Windows**

| Thông tin | GUI Installation | CLI Installation |
|-----------|------------------|------------------|
| *Install* |  |  |
| *Uninstall* |  |  |

**macOS**

| Thông tin | GUI Installation | CLI Installation |
|-----------|------------------|------------------|
| *Install* |  |  |
| *Uninstall* |  |  |

**Linux**

| Thông tin | GUI Installation | CLI Installation |
|-----------|------------------|------------------|
| *Install* |  |  |
| *Uninstall* |  |  |

**Verify:**

    ```bash

    ```
---

## 4. Infrastructure as Code

### 4.1 Terraform

| Thông tin | Link |
|-----------|------|
| **Download** | [terraform.io](https://developer.hashicorp.com/terraform/downloads) |
| **Windows** | `choco install terraform` |
| **macOS** | `brew install terraform` |

**Verify:**

```bash
terraform version
```

---

### 4.2 Ansible

| Thông tin | Link |
|-----------|------|
| **Tài liệu** | [docs.ansible.com](https://docs.ansible.com/ansible/latest/installation_guide/index.html) |
| **Install** | `pip install ansible` |

---

## 5. CI/CD Tools

### 5.1 Jenkins

| Thông tin | Link |
|-----------|------|
| **Download** | [jenkins.io](https://www.jenkins.io/download/) |
| **Docker** | `docker run -p 8080:8080 jenkins/jenkins:lts` |

---

### 5.2 GitHub CLI

| Thông tin | Link |
|-----------|------|
| **Download** | [cli.github.com](https://cli.github.com/) |
| **Windows** | `choco install gh` |
| **macOS** | `brew install gh` |

---

## 6. Monitoring & Logging

### 6.1 Prometheus + Grafana (via Docker)

```bash
# Prometheus
docker run -d -p 9090:9090 prom/prometheus

# Grafana
docker run -d -p 3000:3000 grafana/grafana
```

---

## 7. Cloud CLIs

### 7.1 AWS CLI

| Thông tin | Link |
|-----------|------|
| **Download** | [aws.amazon.com/cli](https://aws.amazon.com/cli/) |
| **Install** | `pip install awscli` |

**Configure:**

```bash
aws configure
```

---

### 7.2 Azure CLI

| Thông tin | Link |
|-----------|------|
| **Download** | [docs.microsoft.com](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli) |

---

### 7.3 Google Cloud CLI

| Thông tin | Link |
|-----------|------|
| **Download** | [cloud.google.com/sdk](https://cloud.google.com/sdk/docs/install) |

---

## 8. Utilities

### 8.1 jq (JSON processor)

```bash
# macOS
brew install jq

# Linux
sudo apt install jq

# Windows
choco install jq
```

---

### 8.2 yq (YAML processor)

```bash
# macOS/Linux
pip install yq

# Hoặc
brew install yq
```

---

### 8.3 curl & wget

```bash
# Thường có sẵn trên Linux/macOS
# Windows: choco install curl wget
```

---

## Checklist cài đặt

Trước khi bắt đầu khóa học, đảm bảo đã cài đặt:

- [ ] WSL2 (Windows only)
- [ ] Docker Desktop
- [ ] Git
- [ ] VS Code + Extensions
- [ ] kubectl (từ Track 2)
- [ ] Terraform (từ Track 3)

---

*Cập nhật lần cuối: 2025-12-27*
