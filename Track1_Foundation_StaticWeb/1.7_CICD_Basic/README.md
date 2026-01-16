# ⚙️ Module 1.7: CI/CD Basic

[![Duration](https://img.shields.io/badge/Duration-10--12%20hours-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Beginner--Intermediate-orange?style=flat-square)](.)

> **Continuous Integration / Continuous Deployment** - Automate your development and deployment workflow with GitLab CI/CD.
>
> *Tích hợp liên tục / Triển khai liên tục - Tự động hóa quy trình phát triển và triển khai với GitLab CI/CD.*

---

## 🔀 Platform Options (Lựa chọn nền tảng)

| Platform | Status | File |
|----------|--------|------|
| **GitLab CI/CD** | ⭐ **Primary** *(Chính)* | This file |
| GitHub Actions | Alternative *(Thay thế)* | [README_GITHUB_ACTIONS.md](./README_GITHUB_ACTIONS.md) |

> 💡 **Note:** This module uses GitLab CI/CD as the primary platform. If you're using GitHub, see the [GitHub Actions guide](./README_GITHUB_ACTIONS.md).
>
> *Module này sử dụng GitLab CI/CD làm nền tảng chính. Nếu bạn dùng GitHub, xem hướng dẫn GitHub Actions.*

---

## 🎯 Learning Objectives (Mục tiêu học tập)

After this module, you will (Sau module này, bạn sẽ):

- ✅ Understand what CI/CD is and why it matters *(Hiểu CI/CD là gì và tại sao quan trọng)*
- ✅ Know the difference between CI, Continuous Delivery, and Continuous Deployment *(Phân biệt được CI, Continuous Delivery và Continuous Deployment)*
- ✅ Master core concepts: Pipeline, Stage, Job, Runner, Artifact *(Nắm vững các khái niệm cốt lõi)*
- ✅ Write GitLab CI/CD pipelines from basic to advanced *(Viết pipeline GitLab CI/CD từ cơ bản đến nâng cao)*
- ✅ Build Docker images automatically in pipeline *(Build Docker images tự động trong pipeline)*
- ✅ Set up auto-deployment when pushing code *(Thiết lập triển khai tự động khi push code)*

---

## 📋 Prerequisites (Điều kiện tiên quyết)

Before starting, you should (Trước khi bắt đầu, bạn nên):

- Have completed [Module 1.4 Git & GitLab](../1.4_Git_GitLab/) *(Đã hoàn thành Module 1.4)*
- Have completed [Module 1.5 Docker Fundamentals](../1.5_Docker_Fundamentals/) *(Đã hoàn thành Module 1.5)*
- Have a GitLab account with a repository *(Có tài khoản GitLab với repository)*

---

## 📚 Content (Nội dung)

### 1. What is CI/CD? - The Problem It Solves (CI/CD là gì? - Vấn đề nó giải quyết) - 1 hour

#### 1.1 The Problem Before CI/CD (Vấn đề trước khi có CI/CD)

Imagine a team of 5 developers working on the same project. Each person writes code on their own machine, and only at the deadline do they merge everything together. What happens?

*Hãy tưởng tượng một team 5 developer cùng làm một dự án. Mỗi người viết code trên máy riêng, và chỉ đến deadline mới ghép code lại với nhau. Điều gì sẽ xảy ra?*

**The "Integration Hell" Scenario (Kịch bản "Địa ngục tích hợp"):**

```
Monday (Thứ 2):
  Developer A: Working on login feature (Làm tính năng đăng nhập)
  Developer B: Working on payment feature (Làm tính năng thanh toán)
  Developer C: Fixing homepage UI (Sửa giao diện trang chủ)
  → Everyone works independently, no one tests combined code
    (Mọi người làm độc lập, không ai test code kết hợp)

Friday - Deadline (Thứ 6 - Deadline):
  → Merge all code together (Ghép tất cả code)
  → 💥 CONFLICTS EVERYWHERE! (Xung đột khắp nơi!)
  → Developer A's code breaks Developer B's feature
    (Code của A làm hỏng tính năng của B)
  → Team spends entire weekend fixing bugs
    (Team mất cả cuối tuần để sửa lỗi)
  → Customer complains about delay (Khách hàng phàn nàn vì delay)
```

**This is exactly why CI was created! (Đây chính là lý do CI ra đời!)**

#### 1.2 What is CI? (CI là gì?)

**CI (Continuous Integration)** is a practice where developers frequently merge their code into a shared repository, and an automated system verifies each merge by running builds and tests.

*CI (Tích hợp liên tục) là phương pháp mà các developer thường xuyên merge code vào repository chung, và hệ thống tự động kiểm tra mỗi lần merge bằng cách chạy build và tests.*

> 💡 **Key Philosophy:** Instead of one big merge at the end (Big Bang Integration), developers merge small changes frequently and the system automatically checks if the new code breaks anything.
>
> *Triết lý cốt lõi: Thay vì ghép code một lần cuối dự án, developer merge các thay đổi nhỏ thường xuyên và hệ thống tự động kiểm tra xem code mới có làm hỏng gì không.*

```
┌─────────────────────────────────────────────────────────────────┐
│                    CI WORKFLOW IN PRACTICE                       │
│                    (Quy trình CI trong thực tế)                  │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  Developer completes a small feature (a few hours - 1 day)      │
│  (Developer hoàn thành tính năng nhỏ)                           │
│       │                                                          │
│       ▼                                                          │
│  Git push to repository (Push lên repository)                   │
│       │                                                          │
│       ▼                                                          │
│  ┌────────────────────────────────────────────────────────┐     │
│  │         CI Server runs automatically (trong vài phút)  │     │
│  │  ┌──────────┐  ┌──────────┐  ┌──────────┐            │     │
│  │  │  Build   │→│   Test   │→│   Lint   │            │     │
│  │  │ (biên    │  │ (chạy    │  │ (kiểm   │            │     │
│  │  │  dịch)   │  │  tests)  │  │ cú pháp) │            │     │
│  │  └──────────┘  └──────────┘  └──────────┘            │     │
│  └────────────────────────────────────────────────────────┘     │
│       │                                                          │
│       ▼                                                          │
│  ┌──────────┐     or     ┌─────────────────────────────────┐   │
│  │ ✅ PASS  │            │ ❌ FAIL - Notify developer:     │   │
│  │ Code OK! │            │ "Test X failed due to your code"│   │
│  │          │            │ → Developer fixes immediately   │   │
│  └──────────┘            └─────────────────────────────────┘   │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

**Benefits of CI (Lợi ích của CI):**

| Before CI (Trước CI) | After CI (Sau CI) |
|----------------------|-------------------|
| Find bugs after 1 week *(Phát hiện lỗi sau 1 tuần)* | Find bugs after 5 minutes *(Phát hiện lỗi sau 5 phút)* |
| Debug takes 2 days *(Debug mất 2 ngày)* | Fix in 30 minutes *(Sửa trong 30 phút)* |
| Team blames each other *(Team đổ lỗi nhau)* | System shows exactly which commit *(Hệ thống chỉ rõ commit nào)* |
| Large scary merge requests *(Merge request lớn đáng sợ)* | Small manageable changes *(Thay đổi nhỏ dễ quản lý)* |

#### 1.3 What is CD? (CD là gì?)

After code is integrated and tested, the next step is **delivering code to users**. This is where CD comes in.

*Sau khi code được tích hợp và test, bước tiếp theo là **đưa code đến tay người dùng**. Đây là lúc CD vào cuộc.*

**There are TWO types of CD - many people confuse them (Có HAI loại CD - nhiều người nhầm lẫn):**

| Term | Meaning | Characteristic |
|------|---------|----------------|
| **Continuous Delivery** | Code is always **ready to deploy** *(Code luôn sẵn sàng deploy)* | Requires button click to deploy to production *(Cần click nút để deploy lên production)* |
| **Continuous Deployment** | Code is **automatically deployed** *(Code được tự động deploy)* | Fully automatic, no human intervention *(Hoàn toàn tự động)* |

```
┌─────────────────────────────────────────────────────────────────┐
│                    CONTINUOUS DELIVERY                           │
│                    (Chuyển giao liên tục)                        │
│                                                                  │
│  Code → Build → Test → ✅ → [Artifact ready]                    │
│                                    │                             │
│                                    ▼                             │
│                         Staging (auto) ──────► Production        │
│                                              ⬆️                   │
│                                         Human Approval needed    │
│                                         (Cần phê duyệt thủ công) │
└─────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────┐
│                    CONTINUOUS DEPLOYMENT                         │
│                    (Triển khai liên tục)                         │
│                                                                  │
│  Code → Build → Test → ✅ → Staging (auto) → Production (auto)  │
│                                                                  │
│  No human intervention! (Không cần con người can thiệp!)        │
│  Netflix, Facebook use this approach                             │
│  (Netflix, Facebook dùng cách này)                              │
└─────────────────────────────────────────────────────────────────┘
```

**Why CD matters - Traditional vs CD Deployment (Tại sao CD quan trọng):**

| Traditional Deployment (Triển khai truyền thống) | With CD (Với CD) |
|--------------------------------------------------|------------------|
| SSH into server manually *(SSH vào server thủ công)* | Pipeline does everything *(Pipeline làm tất cả)* |
| Run commands one by one *(Chạy từng lệnh một)* | Automated, consistent *(Tự động, nhất quán)* |
| Easy to make mistakes *(Dễ mắc sai sót)* | Same process every time *(Quy trình giống nhau mọi lúc)* |
| Takes hours *(Mất hàng giờ)* | Takes minutes *(Mất vài phút)* |
| Stressful for Ops team *(Căng thẳng cho team Ops)* | Relaxed, confident *(Thư giãn, tự tin)* |

---

### 2. CI/CD Tools Overview (Tổng quan công cụ CI/CD) - 30 min

There are many CI/CD tools in the market. Each has its own strengths.

*Có nhiều công cụ CI/CD trên thị trường. Mỗi công cụ có ưu điểm riêng.*

| Tool | Characteristics | When to Use |
|------|-----------------|-------------|
| **GitLab CI/CD** ⭐ | Built-in GitLab, powerful, YAML config *(Tích hợp sẵn GitLab)* | GitLab projects |
| **GitHub Actions** | Built-in GitHub, large marketplace *(Tích hợp sẵn GitHub)* | GitHub projects |
| **Jenkins** | Open source, self-hosted, very flexible *(Mã nguồn mở, tự host)* | Enterprise, legacy systems *(Doanh nghiệp, hệ thống cũ)* |
| **CircleCI** | Cloud-based, fast setup *(Cloud, setup nhanh)* | Startups, small teams |
| **Azure DevOps** | Microsoft ecosystem integration *(Tích hợp hệ sinh thái Microsoft)* | Azure, .NET projects |
| **AWS CodePipeline** | Native AWS integration *(Tích hợp AWS)* | AWS-only workloads |

**In this module, we learn GitLab CI/CD because:**

*Trong module này, chúng ta học GitLab CI/CD vì:*

1. Many Vietnamese companies use GitLab *(Nhiều công ty Việt Nam dùng GitLab)*
2. CI/CD is built-in, no extra setup needed *(CI/CD tích hợp sẵn, không cần cài thêm)*
3. 400 free CI/CD minutes per month *(400 phút CI/CD miễn phí mỗi tháng)*
4. Concepts transfer to other tools *(Khái niệm áp dụng được cho công cụ khác)*

---

### 3. GitLab CI/CD Fundamentals (Nền tảng GitLab CI/CD) - 2 hours

#### 3.1 Architecture Overview (Tổng quan kiến trúc)

```
┌─────────────────────────────────────────────────────────────────────┐
│                    GITLAB CI/CD ARCHITECTURE                         │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  📁 Repository (Kho mã nguồn)                                       │
│  │                                                                   │
│  ├── .gitlab-ci.yml  ◄── CI/CD config file (MUST be in root)       │
│  │                       (File cấu hình CI/CD - BẮT BUỘC ở gốc)     │
│  ├── src/                                                            │
│  ├── tests/                                                          │
│  └── Dockerfile                                                      │
│                                                                      │
│  When git push or merge request happens:                            │
│  (Khi có git push hoặc merge request):                              │
│       │                                                              │
│       ▼                                                              │
│  ┌──────────────────────────────────────────────────────────────┐   │
│  │                        PIPELINE                               │   │
│  │  (Created automatically based on .gitlab-ci.yml)             │   │
│  │  (Được tạo tự động dựa trên .gitlab-ci.yml)                  │   │
│  │                                                               │   │
│  │  ┌─────────────────────────────────────────────────────────┐ │   │
│  │  │ STAGE 1: build          (Stages run sequentially)       │ │   │
│  │  │  ┌────────────┐  ┌────────────┐  (Jobs run in parallel) │ │   │
│  │  │  │ build-web  │  │ build-api  │                         │ │   │
│  │  │  └────────────┘  └────────────┘                         │ │   │
│  │  └─────────────────────────────────────────────────────────┘ │   │
│  │                          │                                    │   │
│  │                          ▼                                    │   │
│  │  ┌─────────────────────────────────────────────────────────┐ │   │
│  │  │ STAGE 2: test                                           │ │   │
│  │  │  ┌────────────┐  ┌────────────┐  ┌────────────┐        │ │   │
│  │  │  │ unit-test  │  │ e2e-test   │  │ lint       │        │ │   │
│  │  │  └────────────┘  └────────────┘  └────────────┘        │ │   │
│  │  └─────────────────────────────────────────────────────────┘ │   │
│  │                          │                                    │   │
│  │                          ▼                                    │   │
│  │  ┌─────────────────────────────────────────────────────────┐ │   │
│  │  │ STAGE 3: deploy                                         │ │   │
│  │  │  ┌────────────┐  ┌────────────────┐                    │ │   │
│  │  │  │ staging    │  │ production 🔒  │ ← Manual click      │ │   │
│  │  │  │ (auto)     │  │ (manual)       │   (Click thủ công)  │ │   │
│  │  │  └────────────┘  └────────────────┘                    │ │   │
│  │  └─────────────────────────────────────────────────────────┘ │   │
│  └──────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  RUNNER: Server that executes jobs (can be GitLab.com or self-hosted)│
│          (Server thực thi jobs - có thể là GitLab.com hoặc tự host) │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

#### 3.2 Core Terminology (Thuật ngữ cốt lõi)

| Term | Explanation | Real-world Example |
|------|-------------|-------------------|
| **Pipeline** | Complete CI/CD workflow, created on each event *(Quy trình CI/CD hoàn chỉnh)* | Each push creates a new pipeline *(Mỗi push tạo pipeline mới)* |
| **Stage** | Phase in pipeline, runs **sequentially** *(Giai đoạn, chạy tuần tự)* | Stage "build" must finish before "test" runs *(Stage "build" phải xong trước "test")* |
| **Job** | Specific task in a stage, jobs in same stage run **in parallel** *(Công việc cụ thể, chạy song song)* | "unit-test" and "e2e-test" run at same time *(Chạy cùng lúc)* |
| **Runner** | Server that executes jobs *(Server chạy jobs)* | GitLab.com provides free shared runners *(GitLab.com cung cấp runners miễn phí)* |
| **Artifact** | Files produced by job, can be downloaded or used by other jobs *(Files tạo ra bởi job)* | `dist/` folder after build *(Thư mục dist/ sau khi build)* |
| **Cache** | Files kept between pipelines to speed up *(Files giữ giữa pipelines để tăng tốc)* | `node_modules/` doesn't need reinstall *(Không cần cài lại)* |
| **Variable** | Environment variable used in pipeline *(Biến môi trường dùng trong pipeline)* | `$DATABASE_URL`, `$API_KEY` |

---

### 4. Pipeline Syntax (Cú pháp Pipeline) - 2 hours

#### 4.1 Basic Pipeline Structure (Cấu trúc Pipeline cơ bản)

The `.gitlab-ci.yml` file is the heart of CI/CD. It must be placed in the **repository root**.

*File `.gitlab-ci.yml` là trái tim của CI/CD. Nó phải được đặt ở **thư mục gốc repository**.*

```yaml
# .gitlab-ci.yml - Simplest example (Ví dụ đơn giản nhất)
# GitLab reads this file automatically when you push

# Step 1: Define stages - they run in ORDER (Định nghĩa stages - chạy theo THỨ TỰ)
stages:
  - build      # Stage 1: Compile code (Biên dịch code)
  - test       # Stage 2: Run tests (Chạy tests)
  - deploy     # Stage 3: Deploy (Triển khai)

# Step 2: Define jobs (Định nghĩa jobs)

# Build job - belongs to "build" stage
# (Job build - thuộc stage "build")
build-app:
  stage: build
  image: node:18-alpine    # Run inside node:18 Docker container
                           # (Chạy trong Docker container node:18)
  script:                   # Commands to run (Các lệnh sẽ chạy)
    - echo "Building application..."
    - npm install
    - npm run build
  artifacts:                # Save output for later jobs (Lưu kết quả cho jobs sau)
    paths:
      - dist/               # Save dist/ folder (Lưu thư mục dist/)
    expire_in: 1 hour       # Delete after 1 hour (Xóa sau 1 giờ)

# Test job - belongs to "test" stage
# (Job test - thuộc stage "test")
test-app:
  stage: test
  image: node:18-alpine
  script:
    - npm install
    - npm run test
  dependencies:
    - build-app             # Download artifacts from build-app
                            # (Download artifacts từ build-app)

# Deploy job - belongs to "deploy" stage
# (Job deploy - thuộc stage "deploy")
deploy-app:
  stage: deploy
  script:
    - echo "Deploying to server..."
  only:
    - main                  # Only run on main branch
                            # (Chỉ chạy trên branch main)
```

#### 4.2 Key Syntax Elements (Các thành phần cú pháp chính)

**`stages:`** - Define execution order (Định nghĩa thứ tự thực thi):

```yaml
stages:
  - build     # ① Runs first (Chạy đầu tiên)
  - test      # ② Runs after build SUCCEEDS (Chạy sau khi build THÀNH CÔNG)
  - deploy    # ③ Runs after test SUCCEEDS (Chạy sau khi test THÀNH CÔNG)
```

> ⚠️ **Important:** If a stage FAILS, subsequent stages will NOT run!
>
> *Quan trọng: Nếu stage FAIL, các stages sau sẽ KHÔNG chạy!*

**`image:`** - Docker image to run the job (Docker image để chạy job):

```yaml
build-app:
  image: node:18-alpine    # Use Node.js 18 (Dùng Node.js 18)
  # This job runs INSIDE a Docker container
  # (Job này chạy BÊN TRONG Docker container)
```

**`only:` / `except:`** - Conditional execution (Điều kiện chạy):

```yaml
# Only run on main branch (Chỉ chạy trên branch main)
deploy-production:
  only:
    - main

# Run on all branches EXCEPT main (Chạy trên mọi branch TRỪ main)
deploy-staging:
  except:
    - main
```

**`when:`** - When to trigger (Khi nào trigger):

```yaml
deploy-production:
  when: manual      # Requires manual button click (Cần click nút thủ công)
  # Other options (Các option khác):
  # when: on_success  - Run when previous jobs succeed (default)
  # when: on_failure  - Run when previous jobs fail
  # when: always      - Always run regardless of result
```

---

### 5. Building Docker Images in Pipeline (Build Docker Image trong Pipeline) - 2 hours

One of the most common use cases is building Docker images and pushing to registry.

*Một trong những use case phổ biến nhất là build Docker images và push lên registry.*

#### 5.1 Docker-in-Docker (DinD)

```yaml
build-docker:
  stage: build
  image: docker:latest         # Use Docker image (Dùng Docker image)
  services:
    - docker:dind              # Docker daemon runs as service
                               # (Docker daemon chạy như service)
  variables:
    DOCKER_TLS_CERTDIR: "/certs"
  before_script:
    # Login to GitLab Container Registry
    # (Đăng nhập vào GitLab Container Registry)
    - docker login -u $CI_REGISTRY_USER -p $CI_REGISTRY_PASSWORD $CI_REGISTRY
  script:
    # Build image with commit SHA as tag
    # (Build image với commit SHA làm tag)
    - docker build -t $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA .
    # Push to registry (Push lên registry)
    - docker push $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA
```

#### 5.2 Predefined Variables (Các biến có sẵn)

GitLab provides many built-in variables:

*GitLab cung cấp nhiều biến có sẵn:*

| Variable | Description | Example Value |
|----------|-------------|---------------|
| `$CI_COMMIT_SHA` | Full commit hash *(Mã commit đầy đủ)* | `abc123def456...` |
| `$CI_COMMIT_SHORT_SHA` | Short commit hash *(Mã commit ngắn)* | `abc123de` |
| `$CI_COMMIT_BRANCH` | Current branch name *(Tên branch hiện tại)* | `main`, `feature/login` |
| `$CI_REGISTRY` | GitLab Container Registry URL | `registry.gitlab.com` |
| `$CI_REGISTRY_IMAGE` | Full image path *(Đường dẫn image đầy đủ)* | `registry.gitlab.com/user/project` |

---

### 6. Variables and Secrets (Biến và Secrets) - 1 hour

#### 6.1 Custom Variables (Biến tùy chỉnh)

```yaml
# Define in .gitlab-ci.yml (Định nghĩa trong .gitlab-ci.yml)
variables:
  NODE_ENV: production
  APP_PORT: "3000"

build:
  script:
    - echo "Building for $NODE_ENV environment"
```

#### 6.2 Secret Variables - In GitLab UI (Biến bí mật - Trong giao diện GitLab)

For sensitive values like API keys and passwords, **DO NOT** put them in `.gitlab-ci.yml`.

*Với các giá trị nhạy cảm như API keys và passwords, **KHÔNG** đặt trong `.gitlab-ci.yml`.*

**How to add secret variables (Cách thêm biến bí mật):**

1. Go to **Settings > CI/CD > Variables** *(Vào Settings > CI/CD > Variables)*
2. Click **Add Variable** *(Click Add Variable)*
3. Enter Key and Value *(Nhập Key và Value)*
4. Check options:
   - **Masked**: Hide value in logs *(Ẩn giá trị trong logs)*
   - **Protected**: Only for protected branches *(Chỉ dùng cho protected branches)*

```yaml
deploy:
  script:
    # Use secret variable from GitLab UI
    # (Dùng biến secret từ GitLab UI)
    - echo "$DEPLOY_TOKEN" | docker login --username user --password-stdin registry.example.com
```

---

### 7. Artifacts and Caching (Artifacts và Caching) - 1 hour

#### 7.1 Artifacts - Share Files Between Jobs (Chia sẻ file giữa các jobs)

```yaml
build:
  stage: build
  script:
    - npm install
    - npm run build
  artifacts:
    paths:
      - dist/           # Save dist/ folder (Lưu thư mục dist/)
      - node_modules/
    expire_in: 1 week   # Auto-delete after 1 week (Tự xóa sau 1 tuần)

test:
  stage: test
  script:
    - npm test          # Can use node_modules from build
  dependencies:
    - build             # Download artifacts from "build" job
                        # (Download artifacts từ job "build")
```

#### 7.2 Cache - Speed Up Pipelines (Tăng tốc pipelines)

Cache is different from Artifacts - Cache is **kept between pipelines**.

*Cache khác Artifacts - Cache được **giữ giữa các pipelines**.*

```yaml
# Cache node_modules between pipeline runs
# (Cache node_modules giữa các lần chạy pipeline)
cache:
  key: ${CI_COMMIT_REF_SLUG}  # Cache key based on branch
  paths:
    - node_modules/           # Cache this folder

build:
  script:
    - npm install             # First time: full download
                              # Next times: use cache, much faster!
                              # (Lần đầu: download đầy đủ)
                              # (Lần sau: dùng cache, nhanh hơn nhiều!)
    - npm run build
```

---

### 8. Complete Pipeline Example (Ví dụ Pipeline hoàn chỉnh) - 1 hour

```yaml
# .gitlab-ci.yml - Complete pipeline for a web application
# (.gitlab-ci.yml - Pipeline hoàn chỉnh cho ứng dụng web)

# Define stages (Định nghĩa stages)
stages:
  - build
  - test
  - deploy

# Global variables (Biến toàn cục)
variables:
  IMAGE_TAG: $CI_REGISTRY_IMAGE:$CI_COMMIT_SHORT_SHA

# Cache npm packages (Cache các gói npm)
cache:
  key: ${CI_COMMIT_REF_SLUG}
  paths:
    - node_modules/

# ============== STAGE: BUILD ==============
build:
  stage: build
  image: node:18-alpine
  script:
    - echo "📦 Installing dependencies..."
    - npm ci                    # Use ci instead of install (faster)
                                # (Dùng ci thay vì install - nhanh hơn)
    - echo "🔨 Building application..."
    - npm run build
  artifacts:
    paths:
      - dist/
    expire_in: 1 hour

# ============== STAGE: TEST ==============
test-unit:
  stage: test
  image: node:18-alpine
  script:
    - echo "🧪 Running unit tests..."
    - npm ci
    - npm run test
  dependencies:
    - build

test-lint:
  stage: test
  image: node:18-alpine
  script:
    - echo "🔍 Running linter..."
    - npm ci
    - npm run lint
  allow_failure: true          # Pipeline won't fail if lint fails
                               # (Pipeline không fail nếu lint fail)

# ============== STAGE: DEPLOY ==============
# Build Docker image (Build Docker image)
docker-build:
  stage: deploy
  image: docker:latest
  services:
    - docker:dind
  before_script:
    - docker login -u $CI_REGISTRY_USER -p $CI_REGISTRY_PASSWORD $CI_REGISTRY
  script:
    - echo "🐳 Building Docker image..."
    - docker build -t $IMAGE_TAG .
    - docker push $IMAGE_TAG
    - echo "✅ Pushed image: $IMAGE_TAG"
  only:
    - main
    - develop

# Deploy to Staging - Automatic (Tự động)
deploy-staging:
  stage: deploy
  image: alpine:latest
  script:
    - echo "🚀 Deploying to STAGING..."
    - echo "Image: $IMAGE_TAG"
    # Add your actual deployment commands here
    # (Thêm lệnh deploy thực tế ở đây)
  environment:
    name: staging
    url: https://staging.example.com
  only:
    - develop
  needs:
    - docker-build

# Deploy to Production - Manual approval required
# (Deploy lên Production - Cần phê duyệt thủ công)
deploy-production:
  stage: deploy
  image: alpine:latest
  script:
    - echo "🚀 Deploying to PRODUCTION..."
    - echo "Image: $IMAGE_TAG"
    # Add your actual deployment commands here
    # (Thêm lệnh deploy thực tế ở đây)
  environment:
    name: production
    url: https://example.com
  when: manual                  # Requires manual approval
                                # (Cần phê duyệt thủ công)
  only:
    - main
  needs:
    - docker-build
```

---

## 📝 Module Files (Các file trong Module)

| File | Description |
|------|-------------|
| [README_GITHUB_ACTIONS.md](./README_GITHUB_ACTIONS.md) | GitHub Actions alternative guide *(Hướng dẫn GitHub Actions)* |
| [CHEATSHEET.md](./CHEATSHEET.md) | Quick reference *(Tra cứu nhanh)* |
| [LABS.md](./LABS.md) | Hands-on labs *(Bài thực hành)* |
| [QUIZ.md](./QUIZ.md) | Knowledge check *(Kiểm tra kiến thức)* |
| [EXERCISES.md](./EXERCISES.md) | Exercises *(Bài tập)* |
| [PROJECT.md](./PROJECT.md) | Mini project *(Dự án nhỏ)* |
| [SOLUTIONS.md](./SOLUTIONS.md) | Solutions *(Đáp án)* |

---

## 🔗 Resources (Tài nguyên)

### Official Documentation (Tài liệu chính thức)

- [GitLab CI/CD Documentation](https://docs.gitlab.com/ee/ci/) - Complete documentation *(Tài liệu đầy đủ)*
- [GitLab CI/CD YAML Reference](https://docs.gitlab.com/ee/ci/yaml/) - Syntax reference *(Tra cứu cú pháp)*
- [Predefined Variables](https://docs.gitlab.com/ee/ci/variables/predefined_variables.html) - List of built-in variables *(Danh sách biến có sẵn)*

### Free Resources (Tài nguyên miễn phí)

- GitLab.com provides **400 free CI/CD minutes/month** *(GitLab.com cung cấp 400 phút CI/CD miễn phí/tháng)*
- Or set up your own [GitLab Runner](https://docs.gitlab.com/runner/) *(Hoặc cài GitLab Runner riêng)*

---

## 💡 Troubleshooting (Xử lý sự cố)

| Issue | Solution |
|-------|----------|
| `Pipeline stuck at pending` | Check if runners are available *(Kiểm tra runners có sẵn không)* |
| `yaml invalid` | Check YAML syntax, use CI Lint *(Kiểm tra cú pháp YAML)* |
| `Docker: command not found` | Use `image: docker:latest` with `services: docker:dind` |
| `Permission denied` | Check variable permissions in Settings *(Kiểm tra quyền biến trong Settings)* |
| `Artifact not found` | Check `artifacts:paths` and `dependencies` *(Kiểm tra paths và dependencies)* |

---

<div align="center">

## 🔗 Module Navigation (Điều hướng Module)

| ← Previous | Current | Next → |
|:----------:|:-------:|:------:|
| [1.6 NGINX](../1.6_NGINX_Basic/) | **1.7 CI/CD** | [1.8 Capstone](../1.8_Capstone_Project/) |

---

**Master CI/CD to accelerate your DevOps career! 🚀**

*Thành thạo CI/CD để đẩy nhanh sự nghiệp DevOps của bạn!*

</div>
