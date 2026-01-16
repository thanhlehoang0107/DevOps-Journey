# ⚙️ Module 1.7: CI/CD Basic

[![Duration](https://img.shields.io/badge/Duration-10--12%20hours-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Beginner--Intermediate-orange?style=flat-square)](.)

> **Continuous Integration / Continuous Deployment** - Tự động hóa quy trình phát triển và triển khai phần mềm với GitLab CI/CD.

---

## 🔀 Platform Options (Lựa chọn nền tảng)

| Platform | Status | File |
|----------|--------|------|
| **GitLab CI/CD** | ⭐ **Primary (Chính)** | This file |
| GitHub Actions | Alternative | [README_GITHUB_ACTIONS.md](./README_GITHUB_ACTIONS.md) |

> 💡 **Note:** Module này sử dụng GitLab CI/CD làm nền tảng chính. Nếu bạn dùng GitHub, xem [hướng dẫn GitHub Actions](./README_GITHUB_ACTIONS.md).

---

## 🎯 Learning Objectives (Mục tiêu học tập)

Sau module này, bạn sẽ:

- ✅ Hiểu **CI/CD là gì**, **tại sao nó quan trọng** và **vấn đề gì nó giải quyết**
- ✅ Nắm vững các khái niệm cốt lõi: Pipeline, Job, Stage, Artifact, Runner
- ✅ Viết được pipeline GitLab CI/CD từ cơ bản đến nâng cao
- ✅ Build Docker images trong pipeline một cách tự động
- ✅ Thiết lập auto deploy khi push code

---

## 📚 Nội dung chi tiết

### 1. CI/CD là gì? - Hiểu bản chất, không chỉ định nghĩa

#### 1.1 Vấn đề trước khi có CI/CD

Hãy tưởng tượng bạn làm việc trong một team 5 developer. Mỗi người viết code trên máy riêng, và khi đến hạn deadline, mọi người mới ghép code lại với nhau. Điều gì sẽ xảy ra?

**Kịch bản thực tế - "Integration Hell" (Địa ngục tích hợp):**

```
Thứ 2: 
  - Dev A viết tính năng đăng nhập
  - Dev B viết tính năng thanh toán  
  - Dev C sửa giao diện trang chủ
  - Mọi người làm việc độc lập, không ai test code chung

Thứ 6 (Deadline):
  - Ghép code lại → 💥 CONFLICT EVERYWHERE!
  - Code của A làm hỏng tính năng của B
  - Giao diện của C không hiển thị đúng với logic mới
  - Team mất 2 ngày cuối tuần để fix bugs
  - Khách hàng phàn nàn vì delay
```

**Đây chính là lý do CI ra đời!**

---

#### 1.2 CI - Continuous Integration (Tích hợp liên tục)

**CI không chỉ là "tích hợp liên tục" - mà là một văn hóa làm việc:**

> **Triết lý:** Thay vì ghép code cuối dự án (Big Bang Integration), các developer **merge code về repository chính thường xuyên** (ít nhất 1 lần/ngày) và **hệ thống tự động kiểm tra** xem code mới có phá vỡ code cũ không.

**Cách CI giải quyết vấn đề "Integration Hell":**

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    QUY TRÌNH CI TRONG THỰC TẾ                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Developer viết xong 1 tính năng nhỏ (vài giờ - 1 ngày)                 │
│       │                                                                  │
│       ▼                                                                  │
│  Git push lên repository                                                 │
│       │                                                                  │
│       ▼                                                                  │
│  ┌────────────────────────────────────────────────────────────────┐     │
│  │              CI Server tự động chạy (trong vài phút)           │     │
│  │  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────────┐   │     │
│  │  │  Build   │→│   Test   │→│   Lint   │→│  Security    │   │     │
│  │  │ (biên    │  │ (chạy    │  │ (kiểm   │  │  Scan        │   │     │
│  │  │  dịch)   │  │  tests)  │  │  cú pháp)│  │ (quét lỗ    │   │     │
│  │  │          │  │          │  │          │  │  hổng)       │   │     │
│  │  └──────────┘  └──────────┘  └──────────┘  └──────────────┘   │     │
│  └────────────────────────────────────────────────────────────────┘     │
│       │                                                                  │
│       ▼                                                                  │
│  ┌──────────────┐  hoặc  ┌──────────────────────────────────────────┐   │
│  │ ✅ PASS      │        │ ❌ FAIL - Thông báo ngay cho developer    │   │
│  │ Code OK!     │        │ "Test case X failed vì code của bạn"     │   │
│  │ Merge được!  │        │ → Developer fix ngay khi vấn đề còn nhỏ  │   │
│  └──────────────┘        └──────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

**Lợi ích thực tế của CI:**

| Trước CI | Sau CI |
|----------|--------|
| Phát hiện lỗi sau 1 tuần, khi đã viết thêm 1000 dòng code | Phát hiện lỗi sau 5 phút, khi chỉ mới thay đổi 50 dòng |
| Debug mất 2 ngày vì không biết lỗi từ đâu | Fix trong 30 phút vì biết chính xác commit nào gây lỗi |
| Team blame nhau vì code của ai làm hỏng | Hệ thống chỉ rõ commit nào, ai push, lúc nào |
| Code review căng thẳng vì merge request quá lớn | Code review nhẹ nhàng vì mỗi MR chỉ 50-100 dòng |

---

#### 1.3 CD - Continuous Delivery / Continuous Deployment

Sau khi code được tích hợp và test thành công, bước tiếp theo là **đưa code đến tay người dùng**. Đây là lúc CD vào cuộc.

**Có 2 khái niệm CD - nhiều người nhầm lẫn:**

| Thuật ngữ | Ý nghĩa | Đặc điểm |
|-----------|---------|----------|
| **Continuous Delivery** (Chuyển giao liên tục) | Code luôn ở trạng thái **sẵn sàng deploy** | Cần click nút để deploy lên production |
| **Continuous Deployment** (Triển khai liên tục) | Code được **tự động deploy** khi pass tests | Hoàn toàn tự động, không cần intervention |

**Minh họa sự khác biệt:**

```
┌─────────────────────────────────────────────────────────────────┐
│                CONTINUOUS DELIVERY                               │
│                                                                  │
│  Code → Build → Test → ✅ → [Artifact sẵn sàng]                 │
│                                    │                             │
│                                    ▼                             │
│                         Staging (auto) ──────► Production        │
│                                              ⬆️                   │
│                                         Cần Human Approval       │
│                                         "Nhấn nút để deploy"     │
└─────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────┐
│                CONTINUOUS DEPLOYMENT                             │
│                                                                  │
│  Code → Build → Test → ✅ → Staging (auto) → Production (auto)  │
│                                                                  │
│  Không cần intervention của con người!                          │
│  Netflix, Facebook dùng cách này - deploy hàng ngàn lần/ngày    │
└─────────────────────────────────────────────────────────────────┘
```

**Tại sao cần CD?**

Hãy tưởng tượng quy trình deploy truyền thống:

```
1. Dev: "Code xong rồi, deploy đi!"
2. Ops: "OK, để tôi SSH vào server..."
3. Ops: "git pull... npm install... restart service..."
4. Ops: "Lỗi rồi! Missing environment variable!"
5. Dev: "À quên, phải set BIẾN_ABC..."
6. Ops: "OK... restart lại... vẫn lỗi!"
7. (Sau 2 tiếng debug)
8. Ops: "Deploy xong rồi!"
9. (Lặp lại mỗi lần deploy - mệt mỏi, dễ sai sót)
```

**Với CD:**

```
1. Dev push code lên branch main
2. Pipeline tự động chạy: build → test → deploy
3. 10 phút sau: code đã live trên production
4. Nếu có lỗi: pipeline fail, thông báo Slack, không deploy
5. (Quy trình giống hệt nhau mỗi lần - không sai sót)
```

---

#### 1.4 DevOps và CI/CD - Mối quan hệ

CI/CD là **một trong những trụ cột quan trọng nhất của DevOps**:

```
┌───────────────────────────────────────────────────────────────────┐
│                       DEVOPS PILLARS                               │
├───────────────────────────────────────────────────────────────────┤
│                                                                    │
│   ┌──────────────┐  ┌──────────────┐  ┌──────────────┐           │
│   │   Culture    │  │   Process    │  │    Tools     │           │
│   │  (Văn hóa)   │  │  (Quy trình) │  │ (Công cụ)    │           │
│   ├──────────────┤  ├──────────────┤  ├──────────────┤           │
│   │ Collaboration│  │   CI/CD ⭐   │  │ GitLab CI    │           │
│   │ Shared       │  │   Agile      │  │ Jenkins      │           │
│   │ Responsibility│ │   IaC        │  │ Docker       │           │
│   │ Continuous   │  │   Monitoring │  │ Kubernetes   │           │
│   │ Improvement  │  │              │  │ Terraform    │           │
│   └──────────────┘  └──────────────┘  └──────────────┘           │
│                                                                    │
│   DevOps = Culture + Process + Tools                              │
│   CI/CD là QUY TRÌNH cốt lõi, được thực hiện bằng TOOLS           │
│                                                                    │
└───────────────────────────────────────────────────────────────────┘
```

---

### 2. Tổng quan về các công cụ CI/CD

Trên thị trường có rất nhiều công cụ CI/CD. Mỗi công cụ có ưu/nhược điểm riêng:

| Công cụ | Đặc điểm | Khi nào nên dùng |
|---------|----------|------------------|
| **GitLab CI/CD** ⭐ | Tích hợp sẵn trong GitLab, cấu hình bằng YAML, miễn phí 400 phút/tháng | Dùng GitLab làm repository |
| **GitHub Actions** | Tích hợp sẵn trong GitHub, marketplace phong phú | Dùng GitHub làm repository |
| **Jenkins** | Open source, tự host, cực kỳ linh hoạt, có từ lâu đời | Doanh nghiệp lớn, cần kiểm soát hoàn toàn, hệ thống legacy |
| **CircleCI** | Cloud-based, nhanh, dễ dùng | Startup, team nhỏ muốn setup nhanh |
| **Azure DevOps** | Tích hợp với hệ sinh thái Microsoft | Công ty dùng Azure, .NET |
| **AWS CodePipeline** | Tích hợp với AWS services | Workload chạy hoàn toàn trên AWS |

**Trong module này, chúng ta học GitLab CI/CD vì:**
1. GitLab là nền tảng được nhiều doanh nghiệp Việt Nam sử dụng
2. CI/CD tích hợp sẵn, không cần cài đặt thêm
3. Có 400 phút CI/CD miễn phí mỗi tháng
4. Concepts tương tự các công cụ khác - học 1 biết nhiều

---

### 3. GitLab CI/CD - Các khái niệm cốt lõi

Trước khi viết code, bạn cần hiểu rõ các thuật ngữ:

#### 3.1 Kiến trúc tổng quan

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    GITLAB CI/CD ARCHITECTURE                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  📁 Repository (Kho mã nguồn)                                           │
│  │                                                                       │
│  ├── .gitlab-ci.yml  ◄── File cấu hình CI/CD (BẮT BUỘC ở thư mục gốc)  │
│  ├── src/                                                                │
│  ├── tests/                                                              │
│  └── Dockerfile                                                          │
│                                                                          │
│  Khi có git push hoặc merge request:                                    │
│       │                                                                  │
│       ▼                                                                  │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │                        PIPELINE                                   │   │
│  │  (Được tạo tự động dựa trên .gitlab-ci.yml)                      │   │
│  │                                                                   │   │
│  │  ┌─────────────────────────────────────────────────────────────┐ │   │
│  │  │ STAGE 1: build                    (Chạy tuần tự)            │ │   │
│  │  │  ┌────────────┐  ┌────────────┐   (Jobs chạy song song)     │ │   │
│  │  │  │ build-web  │  │ build-api  │                             │ │   │
│  │  │  └────────────┘  └────────────┘                             │ │   │
│  │  └─────────────────────────────────────────────────────────────┘ │   │
│  │                          │                                        │   │
│  │                          ▼                                        │   │
│  │  ┌─────────────────────────────────────────────────────────────┐ │   │
│  │  │ STAGE 2: test                                               │ │   │
│  │  │  ┌────────────┐  ┌────────────┐  ┌────────────┐            │ │   │
│  │  │  │ unit-test  │  │ e2e-test   │  │ lint       │            │ │   │
│  │  │  └────────────┘  └────────────┘  └────────────┘            │ │   │
│  │  └─────────────────────────────────────────────────────────────┘ │   │
│  │                          │                                        │   │
│  │                          ▼                                        │   │
│  │  ┌─────────────────────────────────────────────────────────────┐ │   │
│  │  │ STAGE 3: deploy                                             │ │   │
│  │  │  ┌────────────┐  ┌────────────────┐                        │ │   │
│  │  │  │ staging    │  │ production 🔒  │ ← Cần click thủ công   │ │   │
│  │  │  │ (auto)     │  │ (manual)       │                        │ │   │
│  │  │  └────────────┘  └────────────────┘                        │ │   │
│  │  └─────────────────────────────────────────────────────────────┘ │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│  RUNNER: Server thực thi các jobs (có thể là GitLab.com hoặc self-hosted)│
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

#### 3.2 Bảng thuật ngữ chi tiết

| Thuật ngữ | Giải thích | Ví dụ thực tế |
|-----------|------------|---------------|
| **Pipeline** | Toàn bộ quy trình CI/CD, được tạo mỗi khi có sự kiện (push, MR) | Mỗi lần push code tạo 1 pipeline mới |
| **Stage** | Giai đoạn trong pipeline, chạy **tuần tự** (build → test → deploy) | Stage "build" phải xong trước khi "test" chạy |
| **Job** | Công việc cụ thể trong stage, các jobs trong cùng stage chạy **song song** | Job "unit-test" và "e2e-test" chạy cùng lúc |
| **Runner** | Server/máy chạy các jobs | GitLab.com cung cấp shared runners miễn phí |
| **Artifact** | File được tạo ra bởi job, có thể download hoặc dùng cho job khác | File `dist/` sau khi build, dùng cho deploy |
| **Cache** | File được lưu giữa các pipelines để tăng tốc | `node_modules/` không cần install lại mỗi lần |
| **Variable** | Biến môi trường dùng trong pipeline | `$DATABASE_URL`, `$API_KEY` |

---

### 4. Cú pháp GitLab CI/CD Pipeline

#### 4.1 File `.gitlab-ci.yml` - Tim của CI/CD

Đây là file cấu hình duy nhất bạn cần tạo. Đặt ở **thư mục gốc** của repository.

**Ví dụ cơ bản nhất:**

```yaml
# .gitlab-ci.yml - Ví dụ đơn giản nhất
# GitLab sẽ tự động đọc file này khi có push

# Bước 1: Định nghĩa các stages (giai đoạn) - chạy theo THỨ TỰ này
stages:
  - build      # Giai đoạn 1: Biên dịch code
  - test       # Giai đoạn 2: Chạy tests
  - deploy     # Giai đoạn 3: Triển khai

# Bước 2: Định nghĩa các jobs

# Job build - thuộc stage "build"
build-app:
  stage: build
  image: node:18-alpine    # Chạy trong Docker container node:18
  script:                   # Các lệnh sẽ chạy
    - echo "Đang build ứng dụng..."
    - npm install
    - npm run build
  artifacts:                # Lưu kết quả để dùng cho jobs sau
    paths:
      - dist/               # Thư mục dist/ sẽ được lưu
    expire_in: 1 hour       # Xóa sau 1 giờ

# Job test - thuộc stage "test"
test-app:
  stage: test
  image: node:18-alpine
  script:
    - npm install
    - npm run test
  dependencies:
    - build-app             # Download artifacts từ build-app

# Job deploy - thuộc stage "deploy"
deploy-app:
  stage: deploy
  script:
    - echo "Đang deploy lên server..."
  only:
    - main                  # Chỉ chạy khi push lên branch main
```

#### 4.2 Giải thích từng phần

**`stages:`** - Định nghĩa thứ tự các giai đoạn

```yaml
stages:
  - build     # ① Chạy đầu tiên
  - test      # ② Chạy sau khi build THÀNH CÔNG
  - deploy    # ③ Chạy sau khi test THÀNH CÔNG
```

> ⚠️ **Quan trọng:** Nếu stage trước FAIL, các stages sau sẽ KHÔNG chạy!

**`image:`** - Docker image để chạy job

```yaml
build-app:
  image: node:18-alpine    # Dùng Node.js 18
  # Job này chạy TRONG container Docker
```

**`script:`** - Các lệnh shell sẽ thực thi

```yaml
script:
  - npm install            # Lệnh 1
  - npm run build          # Lệnh 2
  - echo "Done!"           # Lệnh 3
```

**`artifacts:`** - Lưu file để dùng cho jobs khác

```yaml
artifacts:
  paths:
    - dist/                # Lưu thư mục dist/
    - coverage/            # Lưu báo cáo coverage
  expire_in: 1 week        # Giữ 1 tuần rồi tự xóa
```

**`only:` / `except:`** - Điều kiện chạy job

```yaml
# Chỉ chạy trên branch main
deploy-production:
  only:
    - main

# Chạy trên mọi branch TRỪ main
deploy-staging:
  except:
    - main
```

**`when:`** - Khi nào job được trigger

```yaml
deploy-production:
  when: manual      # Cần click nút thủ công
  # Các options khác:
  # when: on_success  - Chạy khi jobs trước thành công (mặc định)
  # when: on_failure  - Chạy khi jobs trước fail
  # when: always      - Luôn chạy bất kể kết quả
```

---

### 5. Build Docker Image trong Pipeline

Một trong những use case phổ biến nhất là build Docker image và push lên registry.

#### 5.1 Docker-in-Docker (DinD)

```yaml
build-docker:
  stage: build
  image: docker:latest         # Dùng Docker image
  services:
    - docker:dind              # Docker daemon chạy như service
  variables:
    DOCKER_TLS_CERTDIR: "/certs"
  before_script:
    # Login vào GitLab Container Registry
    - docker login -u $CI_REGISTRY_USER -p $CI_REGISTRY_PASSWORD $CI_REGISTRY
  script:
    # Build image với tag là commit SHA
    - docker build -t $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA .
    # Push lên registry
    - docker push $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA
```

**Giải thích các biến có sẵn:**

| Biến | Giá trị | Ví dụ |
|------|---------|-------|
| `$CI_REGISTRY` | URL của GitLab Container Registry | `registry.gitlab.com` |
| `$CI_REGISTRY_USER` | Username để login | `gitlab-ci-token` |
| `$CI_REGISTRY_PASSWORD` | Password (tự động tạo) | `xxxxx` |
| `$CI_REGISTRY_IMAGE` | Đường dẫn image | `registry.gitlab.com/user/project` |
| `$CI_COMMIT_SHA` | Mã commit đầy đủ | `abc123def456...` |

---

### 6. Variables và Secrets

#### 6.1 Các biến có sẵn (Predefined Variables)

GitLab cung cấp rất nhiều biến có sẵn:

| Biến | Mô tả | Ví dụ giá trị |
|------|-------|---------------|
| `$CI_COMMIT_SHA` | Mã commit đầy đủ (40 ký tự) | `abc123def456789...` |
| `$CI_COMMIT_SHORT_SHA` | Mã commit ngắn (8 ký tự) | `abc123de` |
| `$CI_COMMIT_BRANCH` | Tên branch hiện tại | `main`, `feature/login` |
| `$CI_COMMIT_REF_NAME` | Tên branch hoặc tag | `main`, `v1.0.0` |
| `$CI_PROJECT_NAME` | Tên project | `my-app` |
| `$CI_PIPELINE_ID` | ID của pipeline | `123456` |
| `$CI_JOB_NAME` | Tên job đang chạy | `build-app` |

#### 6.2 Biến tùy chỉnh

```yaml
# Định nghĩa trong file .gitlab-ci.yml
variables:
  NODE_ENV: production
  APP_PORT: "3000"
  DATABASE_NAME: myapp_db

build:
  script:
    - echo "Building for $NODE_ENV environment"
    - echo "App will run on port $APP_PORT"
```

#### 6.3 Secret Variables - Bảo mật với GitLab UI

Đối với các biến nhạy cảm như API keys, passwords, **KHÔNG** đặt trong file `.gitlab-ci.yml`:

1. Vào **Settings > CI/CD > Variables**
2. Click **Add Variable**
3. Nhập Key (ví dụ: `DEPLOY_TOKEN`) và Value
4. Check các options:
   - **Masked**: Ẩn giá trị trong logs
   - **Protected**: Chỉ dùng cho protected branches
   - **Expanded**: Cho phép reference biến khác

```yaml
deploy:
  script:
    # Dùng biến secret từ GitLab UI
    - echo "$DEPLOY_TOKEN" | docker login --username user --password-stdin registry.example.com
```

---

### 7. Artifacts và Caching

#### 7.1 Artifacts - Chia sẻ file giữa các jobs

```yaml
build:
  stage: build
  script:
    - npm install
    - npm run build
  artifacts:
    paths:
      - dist/           # Lưu thư mục dist/
      - node_modules/   # Lưu node_modules
    expire_in: 1 week   # Tự xóa sau 1 tuần

test:
  stage: test
  script:
    - npm test          # Có thể dùng node_modules từ build
  dependencies:
    - build             # Khai báo download artifacts từ job "build"
```

#### 7.2 Cache - Tăng tốc pipelines

Cache khác với Artifacts - Cache được **giữ giữa các pipelines** để không phải download lại dependencies:

```yaml
# Cache node_modules giữa các lần chạy pipeline
cache:
  key: ${CI_COMMIT_REF_SLUG}  # Key cache theo branch
  paths:
    - node_modules/            # Cache thư mục này

build:
  script:
    - npm install             # Lần đầu: download đầy đủ
                               # Lần sau: dùng cache, nhanh hơn nhiều!
    - npm run build
```

---

### 8. Ví dụ Pipeline hoàn chỉnh

Đây là pipeline thực tế cho một ứng dụng web:

```yaml
# .gitlab-ci.yml - Pipeline hoàn chỉnh cho Static Website

# Định nghĩa stages
stages:
  - build
  - test
  - deploy

# Biến toàn cục
variables:
  IMAGE_TAG: $CI_REGISTRY_IMAGE:$CI_COMMIT_SHORT_SHA

# Cache npm packages
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
    - npm ci                    # Dùng ci thay vì install (nhanh hơn)
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
  allow_failure: true          # Pipeline không fail nếu lint fail

# ============== STAGE: DEPLOY ==============
# Build Docker image
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

# Deploy to Staging - Tự động
deploy-staging:
  stage: deploy
  image: alpine:latest
  script:
    - echo "🚀 Deploying to STAGING..."
    - echo "Image: $IMAGE_TAG"
    # Thêm lệnh deploy thực tế ở đây
  environment:
    name: staging
    url: https://staging.example.com
  only:
    - develop
  needs:
    - docker-build

# Deploy to Production - Cần approval
deploy-production:
  stage: deploy
  image: alpine:latest
  script:
    - echo "🚀 Deploying to PRODUCTION..."
    - echo "Image: $IMAGE_TAG"
    # Thêm lệnh deploy thực tế ở đây
  environment:
    name: production
    url: https://example.com
  when: manual                  # Cần click nút thủ công
  only:
    - main
  needs:
    - docker-build
```

---

## 📝 Module Files

| File | Mô tả |
|------|-------|
| [README_GITHUB_ACTIONS.md](./README_GITHUB_ACTIONS.md) | Hướng dẫn GitHub Actions (nếu bạn dùng GitHub) |
| [CHEATSHEET.md](./CHEATSHEET.md) | Tra cứu nhanh cú pháp GitLab CI |
| [LABS.md](./LABS.md) | Bài thực hành step-by-step |
| [QUIZ.md](./QUIZ.md) | Kiểm tra kiến thức |
| [EXERCISES.md](./EXERCISES.md) | Bài tập tự luyện |
| [PROJECT.md](./PROJECT.md) | Dự án thực hành tổng hợp |
| [SOLUTIONS.md](./SOLUTIONS.md) | Đáp án (xem sau khi làm xong) |

---

## 🔗 Tài nguyên học thêm

### Tài liệu chính thức

- [GitLab CI/CD Documentation](https://docs.gitlab.com/ee/ci/) - Tài liệu đầy đủ nhất
- [GitLab CI/CD YAML Reference](https://docs.gitlab.com/ee/ci/yaml/) - Tra cứu cú pháp
- [Predefined Variables](https://docs.gitlab.com/ee/ci/variables/predefined_variables.html) - Danh sách biến có sẵn

### Runners

- GitLab.com cung cấp **400 phút CI/CD miễn phí** mỗi tháng
- Hoặc tự cài [GitLab Runner](https://docs.gitlab.com/runner/) trên máy của bạn

---

<div align="center">

### 🔗 Module Navigation

| ← Trước | Hiện tại | Tiếp theo → |
|:-------:|:--------:|:-----------:|
| [1.6 NGINX](../1.6_NGINX_Basic/) | **1.7 CI/CD** | [1.8 Capstone](../1.8_Capstone_Project/) |

---

**Thành thạo CI/CD - Bước đột phá trong sự nghiệp DevOps! 🚀**

</div>
