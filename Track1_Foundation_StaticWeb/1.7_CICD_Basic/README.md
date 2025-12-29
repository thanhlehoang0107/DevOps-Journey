# ⚙️ Module 1.7: CI/CD Basic

[![Duration](https://img.shields.io/badge/Duration-10--12%20hours-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Beginner--Intermediate-orange?style=flat-square)](.)

> **Continuous Integration / Continuous Deployment** - Automate with GitHub Actions.
>
> *Tích hợp liên tục / Triển khai liên tục với GitHub Actions.*

---

## 🎯 Learning Objectives (Mục tiêu học tập)

After this module, you will (Sau module này, bạn sẽ):

- ✅ Understand what CI/CD is and why it's important (Hiểu CI/CD là gì và tại sao quan trọng)
- ✅ Learn concepts: Pipeline, Job, Step, Artifact (Hiểu các concepts)
- ✅ Write GitHub Actions workflows (Viết workflow GitHub Actions)
- ✅ Build Docker images in pipeline (Build Docker image trong pipeline)
- ✅ Auto deploy when pushing code (Deploy tự động khi push code)

---

## 📖 Nội dung

### 1. CI/CD là gì? (1 giờ)

#### 1.1 Continuous Integration (CI)

```
┌─────────────────────────────────────────────────────────────┐
│                 CONTINUOUS INTEGRATION                       │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  Developer 1 ──┐                                             │
│                │                                             │
│  Developer 2 ──┼──► Git Push ──► CI Pipeline ──► Feedback   │
│                │                    │                        │
│  Developer 3 ──┘                    │                        │
│                                     ▼                        │
│                              ┌──────────────┐               │
│                              │    Build     │               │
│                              ├──────────────┤               │
│                              │    Test      │               │
│                              ├──────────────┤               │
│                              │    Lint      │               │
│                              ├──────────────┤               │
│                              │   Security   │               │
│                              └──────────────┘               │
│                                     │                        │
│                                     ▼                        │
│                              ✅ Pass or ❌ Fail              │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

**CI = Tự động hóa:**

- ✅ Build code
- ✅ Chạy unit tests
- ✅ Chạy linting
- ✅ Security scanning
- ✅ Notify kết quả

#### 1.2 Continuous Delivery (CD)

```
┌─────────────────────────────────────────────────────────────┐
│                 CONTINUOUS DELIVERY                          │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  CI Pipeline ──► Artifacts ──► Deploy Pipeline              │
│                                     │                        │
│                              ┌──────┴──────┐                │
│                              │             │                 │
│                              ▼             ▼                 │
│                        ┌──────────┐ ┌──────────┐            │
│                        │ Staging  │ │   Prod   │            │
│                        │  (auto)  │ │ (manual) │ ← Approval │
│                        └──────────┘ └──────────┘            │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

**CD = Continuous Delivery:**

- Deploy tự động đến staging
- Deploy production cần approval

**CD = Continuous Deployment:**

- Deploy tự động đến tất cả environments

#### 1.3 CI/CD Pipeline

```
┌─────────────────────────────────────────────────────────────┐
│                    FULL CI/CD PIPELINE                       │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│   ┌─────────┐   ┌─────────┐   ┌─────────┐   ┌─────────┐   │
│   │  Code   │──►│  Build  │──►│  Test   │──►│ Deploy  │   │
│   │  Push   │   │         │   │         │   │         │   │
│   └─────────┘   └─────────┘   └─────────┘   └─────────┘   │
│                                                              │
│   Triggers:     Jobs:                       Environments:   │
│   - push        - compile                   - staging       │
│   - PR          - unit test                 - production    │
│   - schedule    - integration               - preview       │
│   - manual      - security scan                             │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

---

### 2. CI/CD Tools Overview (30 phút)

| Tool | Đặc điểm | Sử dụng |
|------|----------|---------|
| **GitHub Actions** | Native GitHub, YAML | GitHub projects |
| **GitLab CI** | Native GitLab | GitLab projects |
| **Jenkins** | Self-hosted, flexible | Enterprise, legacy |
| **CircleCI** | Cloud-based, fast | Startups, open source |
| **Travis CI** | Simple, open source | Open source projects |
| **Azure DevOps** | Microsoft ecosystem | Azure, .NET |
| **AWS CodePipeline** | AWS native | AWS workloads |

**Trong module này, chúng ta sẽ học GitHub Actions.**

---

### 3. GitHub Actions Fundamentals (2 giờ)

#### 3.1 Concepts

```
┌─────────────────────────────────────────────────────────────┐
│                GITHUB ACTIONS CONCEPTS                       │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  WORKFLOW (.github/workflows/main.yml)                      │
│  ├── Trigger (on: push, pull_request, schedule)             │
│  │                                                           │
│  └── JOBS (runs in parallel by default)                     │
│      ├── Job 1: build                                        │
│      │   ├── runs-on: ubuntu-latest                         │
│      │   └── STEPS                                           │
│      │       ├── Step 1: Checkout code                      │
│      │       ├── Step 2: Setup Node.js                      │
│      │       ├── Step 3: Install deps                       │
│      │       └── Step 4: Run tests                          │
│      │                                                       │
│      └── Job 2: deploy (needs: build)                       │
│          ├── runs-on: ubuntu-latest                         │
│          └── STEPS                                           │
│              ├── Step 1: Checkout                           │
│              └── Step 2: Deploy to server                   │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

#### 3.2 Terminology

| Term | Description |
|------|-------------|
| **Workflow** | Automated process defined in YAML |
| **Event** | Trigger that starts workflow (push, PR, etc.) |
| **Job** | Set of steps that run on same runner |
| **Step** | Individual task (run command or action) |
| **Action** | Reusable unit (marketplace or custom) |
| **Runner** | Server that runs the jobs |
| **Artifact** | Files produced by job (can share between jobs) |

---

### 4. Workflow Syntax (2 giờ)

#### 4.1 Basic Workflow

```yaml
# .github/workflows/ci.yml

name: CI Pipeline                    # Workflow name

on:                                   # Triggers
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

jobs:                                 # Jobs
  build:                              # Job name
    runs-on: ubuntu-latest            # Runner OS
    
    steps:                            # Steps
      - name: Checkout code
        uses: actions/checkout@v4     # Use an action

      - name: Run a script
        run: echo "Hello World!"      # Run command

      - name: Multi-line script
        run: |
          echo "Line 1"
          echo "Line 2"
          ls -la
```

#### 4.2 Triggers (Events)

```yaml
on:
  # Push to specific branches
  push:
    branches:
      - main
      - 'feature/**'        # Wildcard
    paths:
      - 'src/**'            # Only when src changes
      - '!src/**/*.md'      # Except markdown
    tags:
      - 'v*'                # Tags starting with v

  # Pull requests
  pull_request:
    branches: [main]
    types: [opened, synchronize, reopened]

  # Schedule (cron)
  schedule:
    - cron: '0 0 * * *'     # Daily at midnight UTC

  # Manual trigger
  workflow_dispatch:
    inputs:
      environment:
        description: 'Environment to deploy'
        required: true
        default: 'staging'
```

#### 4.3 Jobs và Dependencies

```yaml
jobs:
  # Job 1: Build
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: npm install
      - run: npm run build

  # Job 2: Test (parallel với build)
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: npm test

  # Job 3: Deploy (sau khi build VÀ test hoàn thành)
  deploy:
    runs-on: ubuntu-latest
    needs: [build, test]          # Dependencies
    if: github.ref == 'refs/heads/main'  # Condition
    steps:
      - run: echo "Deploying..."
```

#### 4.4 Environment Variables và Secrets

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    
    env:                           # Job-level env vars
      NODE_ENV: production
    
    steps:
      - name: Use env vars
        env:                       # Step-level env vars
          API_KEY: ${{ secrets.API_KEY }}
        run: |
          echo "Node env: $NODE_ENV"
          echo "Running with API key..."

      - name: Use GitHub context
        run: |
          echo "Repo: ${{ github.repository }}"
          echo "Branch: ${{ github.ref_name }}"
          echo "SHA: ${{ github.sha }}"
          echo "Actor: ${{ github.actor }}"
```

---

### 5. Common Actions (1.5 giờ)

#### 5.1 Checkout Code

```yaml
- name: Checkout
  uses: actions/checkout@v4
  with:
    fetch-depth: 0        # Full history (for versioning)
```

#### 5.2 Setup Languages

```yaml
# Node.js
- name: Setup Node.js
  uses: actions/setup-node@v4
  with:
    node-version: '18'
    cache: 'npm'

# Python
- name: Setup Python
  uses: actions/setup-python@v5
  with:
    python-version: '3.11'
    cache: 'pip'

# Go
- name: Setup Go
  uses: actions/setup-go@v5
  with:
    go-version: '1.21'
```

#### 5.3 Caching

```yaml
- name: Cache node_modules
  uses: actions/cache@v3
  with:
    path: ~/.npm
    key: ${{ runner.os }}-node-${{ hashFiles('**/package-lock.json') }}
    restore-keys: |
      ${{ runner.os }}-node-
```

#### 5.4 Upload/Download Artifacts

```yaml
# Upload artifact
- name: Upload build
  uses: actions/upload-artifact@v4
  with:
    name: build-output
    path: dist/

# Download artifact (in another job)
- name: Download build
  uses: actions/download-artifact@v4
  with:
    name: build-output
    path: dist/
```

---

### 6. Docker in GitHub Actions (2 giờ)

#### 6.1 Build và Push Docker Image

```yaml
name: Docker Build and Push

on:
  push:
    branches: [main]
    tags: ['v*']

jobs:
  docker:
    runs-on: ubuntu-latest
    
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v3

      - name: Login to Docker Hub
        uses: docker/login-action@v3
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_TOKEN }}

      - name: Extract metadata
        id: meta
        uses: docker/metadata-action@v5
        with:
          images: myuser/myapp
          tags: |
            type=ref,event=branch
            type=ref,event=tag
            type=sha,prefix=

      - name: Build and push
        uses: docker/build-push-action@v5
        with:
          context: .
          push: true
          tags: ${{ steps.meta.outputs.tags }}
          labels: ${{ steps.meta.outputs.labels }}
          cache-from: type=gha
          cache-to: type=gha,mode=max
```

#### 6.2 Build Multi-platform Images

```yaml
- name: Build and push multi-platform
  uses: docker/build-push-action@v5
  with:
    context: .
    platforms: linux/amd64,linux/arm64
    push: true
    tags: myuser/myapp:latest
```

---

### 7. Complete CI/CD Example (2 giờ)

#### 7.1 Static Website CI/CD

```yaml
# .github/workflows/deploy.yml

name: Deploy Static Website

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  # Job 1: Build
  build:
    runs-on: ubuntu-latest
    
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '18'
          cache: 'npm'

      - name: Install dependencies
        run: npm ci

      - name: Run linting
        run: npm run lint

      - name: Run tests
        run: npm test

      - name: Build
        run: npm run build

      - name: Upload build artifact
        uses: actions/upload-artifact@v4
        with:
          name: dist
          path: dist/

  # Job 2: Deploy (only on main branch)
  deploy:
    runs-on: ubuntu-latest
    needs: build
    if: github.ref == 'refs/heads/main' && github.event_name == 'push'
    
    environment:
      name: production
      url: https://example.com
    
    steps:
      - name: Download artifact
        uses: actions/download-artifact@v4
        with:
          name: dist
          path: dist/

      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist
```

#### 7.2 Docker + Deploy Example

```yaml
name: Build and Deploy

on:
  push:
    branches: [main]
    tags: ['v*']

env:
  REGISTRY: ghcr.io
  IMAGE_NAME: ${{ github.repository }}

jobs:
  build:
    runs-on: ubuntu-latest
    permissions:
      contents: read
      packages: write
    
    outputs:
      image-tag: ${{ steps.meta.outputs.tags }}
    
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Log in to Container Registry
        uses: docker/login-action@v3
        with:
          registry: ${{ env.REGISTRY }}
          username: ${{ github.actor }}
          password: ${{ secrets.GITHUB_TOKEN }}

      - name: Extract metadata
        id: meta
        uses: docker/metadata-action@v5
        with:
          images: ${{ env.REGISTRY }}/${{ env.IMAGE_NAME }}

      - name: Build and push
        uses: docker/build-push-action@v5
        with:
          context: .
          push: true
          tags: ${{ steps.meta.outputs.tags }}
          labels: ${{ steps.meta.outputs.labels }}

  deploy:
    runs-on: ubuntu-latest
    needs: build
    if: github.ref == 'refs/heads/main'
    
    steps:
      - name: Deploy to server
        uses: appleboy/ssh-action@v1.0.0
        with:
          host: ${{ secrets.SERVER_HOST }}
          username: ${{ secrets.SERVER_USER }}
          key: ${{ secrets.SERVER_SSH_KEY }}
          script: |
            docker pull ${{ env.REGISTRY }}/${{ env.IMAGE_NAME }}:main
            docker stop myapp || true
            docker rm myapp || true
            docker run -d --name myapp -p 80:80 ${{ env.REGISTRY }}/${{ env.IMAGE_NAME }}:main
```

---

### 8. Best Practices (1 giờ)

#### 8.1 Security

```yaml
# Sử dụng specific versions
- uses: actions/checkout@v4.1.1  # Không dùng @main

# Limit permissions
permissions:
  contents: read
  packages: write

# Sử dụng secrets đúng cách
env:
  API_KEY: ${{ secrets.API_KEY }}

# Không log secrets
run: |
  # ❌ Bad
  echo ${{ secrets.API_KEY }}
  
  # ✅ Good
  echo "Using API key..."
```

#### 8.2 Performance

```yaml
# Sử dụng caching
- uses: actions/cache@v3
  with:
    path: ~/.npm
    key: ${{ runner.os }}-npm-${{ hashFiles('**/package-lock.json') }}

# Fail fast
strategy:
  fail-fast: true

# Timeout
jobs:
  build:
    runs-on: ubuntu-latest
    timeout-minutes: 10
```

#### 8.3 Organization

```yaml
# Reusable workflows
# .github/workflows/reusable-build.yml
on:
  workflow_call:
    inputs:
      node-version:
        required: true
        type: string

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: ${{ inputs.node-version }}

# Sử dụng reusable workflow
# .github/workflows/main.yml
jobs:
  build:
    uses: ./.github/workflows/reusable-build.yml
    with:
      node-version: '18'
```

---

## 📝 Module Files (Các file trong Module)

| File | Description |
|------|-------------|
| [CHEATSHEET.md](./CHEATSHEET.md) | Quick reference (Tra cứu nhanh) |
| [LABS.md](./LABS.md) | Hands-on labs (Bài thực hành) |
| [QUIZ.md](./QUIZ.md) | Knowledge check (Kiểm tra kiến thức) |
| [EXERCISES.md](./EXERCISES.md) | Exercises (Bài tập) |
| [PROJECT.md](./PROJECT.md) | Mini project (Dự án nhỏ) |
| [SOLUTIONS.md](./SOLUTIONS.md) | Solutions (Đáp án) |

---

<div align="center">

### 🔗 Module Navigation (Điều hướng Module)

| ← Previous | Current | Next → |
|:------------------:|:------------------:|:-------------:|
| [1.6 NGINX](../1.6_NGINX_Basic/) | **1.7 CI/CD** | [1.8 Capstone](../1.8_Capstone_Project/) |

---

**Master CI/CD! ⚙️**

*Thành thạo CI/CD!*

</div>
