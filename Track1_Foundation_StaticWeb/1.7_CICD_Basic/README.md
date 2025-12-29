# ⚙️ Module 1.7: CI/CD Basic

[![Duration](https://img.shields.io/badge/Duration-10--12%20hours-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Beginner--Intermediate-orange?style=flat-square)](.)

> **Continuous Integration / Continuous Deployment** - Automate with GitLab CI/CD.
>
> *Tích hợp liên tục / Triển khai liên tục với GitLab CI/CD.*

---

## 🔀 Platform Options (Lựa chọn nền tảng)

| Platform | Status | File |
|----------|--------|------|
| **GitLab CI/CD** | ⭐ **Primary (Chính)** | This file |
| GitHub Actions | Alternative | [README_GITHUB_ACTIONS.md](./README_GITHUB_ACTIONS.md) |

> 💡 **Note:** This module uses GitLab CI/CD as the primary platform. If you're using GitHub, see the [GitHub Actions guide](./README_GITHUB_ACTIONS.md).
>
> *Module này sử dụng GitLab CI/CD làm nền tảng chính. Nếu bạn dùng GitHub, xem [hướng dẫn GitHub Actions](./README_GITHUB_ACTIONS.md).*

---

## 🎯 Learning Objectives (Mục tiêu học tập)

After this module, you will (Sau module này, bạn sẽ):

- ✅ Understand what CI/CD is and why it's important (Hiểu CI/CD là gì và tại sao quan trọng)
- ✅ Learn concepts: Pipeline, Job, Stage, Artifact (Hiểu các concepts)
- ✅ Write GitLab CI/CD pipelines (Viết pipeline GitLab CI/CD)
- ✅ Build Docker images in pipeline (Build Docker image trong pipeline)
- ✅ Auto deploy when pushing code (Deploy tự động khi push code)

---

## 📖 Content (Nội dung)

### 1. What is CI/CD? (CI/CD là gì?) - 1 hour

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

**CI = Automation of (CI = Tự động hóa):**

- ✅ Build code
- ✅ Run unit tests (Chạy unit tests)
- ✅ Run linting (Chạy linting)
- ✅ Security scanning
- ✅ Notify results (Thông báo kết quả)

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

**Continuous Delivery:**

- Auto deploy to staging (Deploy tự động đến staging)
- Production requires approval (Production cần approval)

**Continuous Deployment:**

- Auto deploy to all environments (Deploy tự động đến tất cả environments)

---

### 2. CI/CD Tools Overview - 30 min

| Tool | Features | Use Case |
|------|----------|----------|
| **GitLab CI/CD** | Native GitLab, powerful | GitLab projects ⭐ |
| **GitHub Actions** | Native GitHub, YAML | GitHub projects |
| **Jenkins** | Self-hosted, flexible | Enterprise, legacy |
| **CircleCI** | Cloud-based, fast | Startups |
| **Azure DevOps** | Microsoft ecosystem | Azure, .NET |
| **AWS CodePipeline** | AWS native | AWS workloads |

**In this module, we learn GitLab CI/CD.**

*Trong module này, chúng ta học GitLab CI/CD.*

---

### 3. GitLab CI/CD Fundamentals - 2 hours

#### 3.1 Concepts (Khái niệm)

```
┌─────────────────────────────────────────────────────────────┐
│                GITLAB CI/CD CONCEPTS                         │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  PIPELINE (.gitlab-ci.yml in root directory)                │
│  ├── Triggered by: push, merge request, schedule            │
│  │                                                           │
│  └── STAGES (run sequentially - chạy tuần tự)               │
│      ├── Stage 1: build                                      │
│      │   └── JOBS (run in parallel within stage)            │
│      │       ├── Job: build-frontend                        │
│      │       └── Job: build-backend                         │
│      │                                                       │
│      ├── Stage 2: test                                       │
│      │   └── JOBS                                            │
│      │       ├── Job: unit-test                             │
│      │       └── Job: integration-test                      │
│      │                                                       │
│      └── Stage 3: deploy                                     │
│          └── JOBS                                            │
│              ├── Job: deploy-staging                        │
│              └── Job: deploy-production (manual)            │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

#### 3.2 Terminology (Thuật ngữ)

| Term | Description |
|------|-------------|
| **Pipeline** | Complete CI/CD process (Quy trình CI/CD hoàn chỉnh) |
| **Stage** | Phase of pipeline - build, test, deploy (Giai đoạn) |
| **Job** | Task that runs in a stage (Công việc trong stage) |
| **Runner** | Server that executes jobs (Server chạy jobs) |
| **Artifact** | Files produced by job (Files tạo ra bởi job) |
| **Cache** | Files cached between pipelines (Files cache giữa các pipeline) |
| **Variable** | Environment variable (Biến môi trường) |

---

### 4. Pipeline Syntax (Cú pháp Pipeline) - 2 hours

#### 4.1 Basic Pipeline (Pipeline cơ bản)

```yaml
# .gitlab-ci.yml <-- in root of repository (đặt ở thư mục gốc repository)

# Define stages - run in order (Định nghĩa stages - chạy theo thứ tự)
stages:
  - build
  - test
  - deploy

# Build job
build:
  stage: build
  image: node:18-alpine
  script:
    - npm install
    - npm run build
  artifacts:
    paths:
      - dist/
    expire_in: 1 hour

# Test job (Job kiểm thử)
test:
  stage: test
  image: node:18-alpine
  script:
    - npm install
    - npm run test
  dependencies:
    - build

# Deploy job (Job triển khai)
deploy:
  stage: deploy
  image: docker:latest
  script:
    - echo "Deploying to server..."
  only:
    - main  # Only run on main branch (Chỉ chạy trên nhánh main)
```

#### 4.2 Key Differences: GitLab CI vs GitHub Actions

| Feature | GitLab CI | GitHub Actions |
|---------|-----------|----------------|
| **Config file** | `.gitlab-ci.yml` | `.github/workflows/*.yml` |
| **Stages** | `stages:` keyword | `jobs:` with `needs:` |
| **Scripts** | `script:` keyword | `run:` keyword |
| **Docker image** | `image:` keyword | `container:` or in step |
| **Conditionals** | `only:`, `except:`, `rules:` | `if:` conditions |
| **Triggers** | Automatic on push | `on:` keyword |

#### 4.3 Stages and Jobs

```yaml
# Stages define ORDER of execution (Stages định nghĩa THỨ TỰ thực thi)
stages:
  - build      # Runs first (Chạy đầu tiên)
  - test       # Runs second - after build completes (Chạy thứ hai - sau khi build hoàn thành)
  - deploy     # Runs third - after test completes (Chạy thứ ba - sau khi test hoàn thành)

# Multiple jobs in same stage run IN PARALLEL (Nhiều jobs trong cùng stage chạy SONG SONG
build-frontend:
  stage: build
  script:
    - npm run build:frontend

build-backend:
  stage: build
  script:
    - npm run build:backend

# Both build jobs run at the same time! (Cả 2 jobs chạy cùng lúc!)
```

#### 4.4 Triggers (Kích hoạt)

```yaml
# Default: runs on every push to any branch (Mặc định: chạy mỗi khi push lên bất kỳ branch nào

# Run only on specific branches (Chỉ chạy trên nhánh cụ thể)
deploy-staging:
  stage: deploy
  script:
    - ./deploy.sh staging
  only:
    - develop

# Run only on main branch (Chỉ chạy trên nhánh main)
deploy-production:
  stage: deploy
  script:
    - ./deploy.sh production
  only:
    - main
  when: manual  # Requires manual click (Cần click thủ công)

# Rules syntax - more powerful (Cú pháp rules - mạnh hơn)
deploy:
  stage: deploy
  script:
    - ./deploy.sh
  rules:
    - if: '$CI_COMMIT_BRANCH == "main"'
      when: manual
    - if: '$CI_COMMIT_BRANCH == "develop"'
      when: on_success
    - when: never  # Don't run on other branches (Không chạy trên nhánh khác)
```

---

### 5. Building Docker Images in Pipeline (Build Docker Image trong Pipeline) - 2 hours

#### 5.1 Docker-in-Docker (DinD)

```yaml
# Build and push Docker image (Build và push Docker image)
build-docker:
  stage: build
  image: docker:latest
  services:
    - docker:dind
  variables:
    DOCKER_TLS_CERTDIR: "/certs"
  before_script:
    - docker login -u $CI_REGISTRY_USER -p $CI_REGISTRY_PASSWORD $CI_REGISTRY
  script:
    - docker build -t $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA .
    - docker push $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA
```

#### 5.2 Using GitLab Container Registry (Sử dụng GitLab Container Registry)

```yaml
variables:
  IMAGE_TAG: $CI_REGISTRY_IMAGE:$CI_COMMIT_REF_SLUG

build:
  stage: build
  image: docker:latest
  services:
    - docker:dind
  script:
    - docker login -u $CI_REGISTRY_USER -p $CI_REGISTRY_PASSWORD $CI_REGISTRY
    - docker build -t $IMAGE_TAG .
    - docker push $IMAGE_TAG

deploy:
  stage: deploy
  image: docker:latest
  script:
    - docker login -u $CI_REGISTRY_USER -p $CI_REGISTRY_PASSWORD $CI_REGISTRY
    - docker pull $IMAGE_TAG
    - docker run -d -p 80:80 $IMAGE_TAG
  only:
    - main  # Only deploy on main branch ()
```

---

### 6. Variables and Secrets (Biến và Secrets) - 1 hour

#### 6.1 Predefined Variables (Biến đã định nghĩa sẵn)

| Variable | Description |
|----------|-------------|
| `$CI_COMMIT_SHA` | Full commit SHA (Mã commit đầy đủ) |
| `$CI_COMMIT_REF_NAME` | Branch or tag name (Tên branch hoặc tag) |
| `$CI_COMMIT_REF_SLUG` | Slug of branch - url-safe (Slug của branch) |
| `$CI_PROJECT_NAME` | Project name (Tên dự án) |
| `$CI_REGISTRY` | GitLab Container Registry URL |
| `$CI_REGISTRY_IMAGE` | Full image path (Đường dẫn image đầy đủ) |
| `$CI_PIPELINE_ID` | Pipeline ID |

#### 6.2 Custom Variables (Biến tùy chỉnh)

```yaml
# Define in .gitlab-ci.yml (Định nghĩa trong .gitlab-ci.yml)
variables:
  NODE_ENV: production
  APP_PORT: "3000"

build:
  stage: build
  script:
    - echo "Building for $NODE_ENV on port $APP_PORT"
```

#### 6.3 Secret Variables - in GitLab UI (Biến bí mật - trong giao diện GitLab)

1. Go to **Settings > CI/CD > Variables** (Vào Settings > CI/CD > Variables)
2. Add variable, e.g., `DEPLOY_TOKEN` (Thêm biến)
3. Check **Masked** to hide in logs (Đánh dấu Masked để ẩn trong logs)
4. Check **Protected** for protected branches only (Đánh dấu Protected cho nhánh được bảo vệ)

```yaml
deploy:
  stage: deploy
  script:
    - echo "$DEPLOY_TOKEN" | docker login -u token --password-stdin registry.example.com
```

---

### 7. Artifacts and Caching (Artifacts và Caching) - 1 hour

#### 7.1 Artifacts - Shared between jobs (Chia sẻ giữa các jobs)

```yaml
build:
  stage: build
  script:
    - npm install
    - npm run build
  artifacts:
    paths:
      - dist/
      - node_modules/
    expire_in: 1 week  # Keep for 1 week (Giữ 1 tuần)

test:
  stage: test
  script:
    - npm test
  dependencies:
    - build  # Download artifacts from build job (Tải artifacts từ job build)
```

#### 7.2 Cache - Shared between pipelines (Chia sẻ giữa các pipelines)

```yaml
# Cache node_modules between pipelines (Cache node_modules giữa các pipelines)
cache:
  key: ${CI_COMMIT_REF_SLUG}
  paths:
    - node_modules/

build:
  stage: build
  script:
    - npm install  # Uses cache if exists (Dùng cache nếu có)
    - npm run build
```

---

### 8. Complete Pipeline Example (Ví dụ Pipeline hoàn chỉnh) - 1 hour

#### Static Website with Docker (Website tĩnh với Docker)

```yaml
# .gitlab-ci.yml - Complete example (Ví dụ hoàn chỉnh)

stages:
  - build
  - test
  - deploy

variables:
  IMAGE_TAG: $CI_REGISTRY_IMAGE:$CI_COMMIT_SHORT_SHA

# Cache npm packages (Cache các gói npm)
cache:
  key: ${CI_COMMIT_REF_SLUG}
  paths:
    - node_modules/

# Build stage (Giai đoạn build)
build:
  stage: build
  image: node:18-alpine
  script:
    - npm ci
    - npm run build
  artifacts:
    paths:
      - dist/
    expire_in: 1 hour

# Test stage (Giai đoạn kiểm thử)
test:
  stage: test
  image: node:18-alpine
  script:
    - npm ci
    - npm run test
    - npm run lint
  dependencies:
    - build

# Build Docker image (Build Docker image)
docker-build:
  stage: deploy
  image: docker:latest
  services:
    - docker:dind
  before_script:
    - docker login -u $CI_REGISTRY_USER -p $CI_REGISTRY_PASSWORD $CI_REGISTRY
  script:
    - docker build -t $IMAGE_TAG .
    - docker push $IMAGE_TAG
  only:
    - main
    - develop

# Deploy to staging - auto (Triển khai staging - tự động)
deploy-staging:
  stage: deploy
  image: alpine:latest
  script:
    - echo "Deploying $IMAGE_TAG to staging..."
    # Add your deployment commands here (Thêm lệnh triển khai ở đây)
  environment:
    name: staging
    url: https://staging.example.com
  only:
    - develop

# Deploy to production - manual (Triển khai production - thủ công)
deploy-production:
  stage: deploy
  image: alpine:latest
  script:
    - echo "Deploying $IMAGE_TAG to production..."
    # Add your deployment commands here (Thêm lệnh triển khai ở đây)
  environment:
    name: production
    url: https://example.com
  when: manual  # Requires manual approval (Cần phê duyệt thủ công)
  only:
    - main
```

---

## 📝 Module Files (Các file trong Module)

| File | Description |
|------|-------------|
| [README_GITHUB_ACTIONS.md](./README_GITHUB_ACTIONS.md) | GitHub Actions alternative guide (Hướng dẫn GitHub Actions) |
| [CHEATSHEET.md](./CHEATSHEET.md) | Quick reference (Tra cứu nhanh) |
| [LABS.md](./LABS.md) | Hands-on labs (Bài thực hành) |
| [QUIZ.md](./QUIZ.md) | Knowledge check (Kiểm tra kiến thức) |
| [EXERCISES.md](./EXERCISES.md) | Exercises (Bài tập) |
| [PROJECT.md](./PROJECT.md) | Mini project (Dự án nhỏ) |
| [SOLUTIONS.md](./SOLUTIONS.md) | Solutions (Đáp án) |

---

## 🔗 Resources (Tài nguyên)

### Official Documentation (Tài liệu chính thức)

- [GitLab CI/CD Documentation](https://docs.gitlab.com/ee/ci/)
- [GitLab CI/CD YAML Reference](https://docs.gitlab.com/ee/ci/yaml/)
- [GitLab Container Registry](https://docs.gitlab.com/ee/user/packages/container_registry/)

### Free GitLab Runners (GitLab Runners miễn phí)

- GitLab.com includes **400 CI/CD minutes/month** on free tier (400 phút CI/CD/tháng miễn phí)
- Or set up your own [GitLab Runner](https://docs.gitlab.com/runner/) (Hoặc cài đặt Runner riêng)

---

<div align="center">

### 🔗 Module Navigation

| ← Previous | Current | Next → |
|:----------:|:-------:|:------:|
| [1.6 NGINX](../1.6_NGINX_Basic/) | **1.7 CI/CD** | [1.8 Capstone](../1.8_Capstone_Project/) |

---

**Master CI/CD with GitLab! 🚀**

*Thành thạo CI/CD với GitLab!*

</div>
