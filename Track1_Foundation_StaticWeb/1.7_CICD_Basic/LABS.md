# 🔬 Labs: CI/CD Basic

> **Hands-on Labs for GitLab CI/CD**
>
> *Bài thực hành GitLab CI/CD.*

---

## 📋 Overview (Tổng quan)

These labs use **GitLab CI** as the primary platform. For GitHub Actions alternative, see [README_GITHUB_ACTIONS.md](./README_GITHUB_ACTIONS.md).

*Các bài lab sử dụng **GitLab CI** làm nền tảng chính. Xem phiên bản GitHub Actions tại [README_GITHUB_ACTIONS.md](./README_GITHUB_ACTIONS.md).*

---

## 🔬 Lab 1: First Pipeline (Pipeline Đầu Tiên)

Create your first GitLab CI pipeline.

*Tạo pipeline GitLab CI đầu tiên.*

```yaml
# .gitlab-ci.yml
stages:
  - hello

hello-job:
  stage: hello
  script:
    - echo "Hello, GitLab CI!"
    - date
    - echo "Running on $CI_RUNNER_EXECUTABLE_ARCH"
    - echo "Project: $CI_PROJECT_NAME"
    - echo "Commit: $CI_COMMIT_SHORT_SHA"
```

### Steps to complete (Các bước thực hiện)

1. Create a new project in GitLab (Tạo project mới trên GitLab)
2. Create `.gitlab-ci.yml` in root directory (Tạo file ở thư mục gốc)
3. Commit and push (Commit và push)
4. Go to **CI/CD > Pipelines** to see result (Vào xem kết quả)

---

## 🔬 Lab 2: Build Stage (Giai đoạn Build)

A pipeline with checkout and build.

*Pipeline với checkout và build.*

```yaml
# .gitlab-ci.yml
stages:
  - build

build-job:
  stage: build
  image: node:18-alpine
  script:
    - node --version
    - npm --version
    - npm install
    - npm run build
  artifacts:
    paths:
      - dist/
    expire_in: 1 hour
```

### Key concepts (Khái niệm quan trọng)

- `image`: Docker image to run job (Docker image để chạy job)
- `artifacts`: Files to save after job (Files lưu lại sau job)
- `expire_in`: How long to keep artifacts (Thời gian giữ artifacts)

---

## 🔬 Lab 3: Testing Pipeline (Pipeline Testing)

Pipeline with testing and coverage report.

*Pipeline với testing và báo cáo coverage.*

```yaml
# .gitlab-ci.yml
stages:
  - test

test-job:
  stage: test
  image: node:18-alpine
  script:
    - npm ci
    - npm test -- --coverage
  coverage: '/All files[^|]*\|[^|]*\s+([\d\.]+)/'
  artifacts:
    when: always
    paths:
      - coverage/
    reports:
      junit: junit.xml
      coverage_report:
        coverage_format: cobertura
        path: coverage/cobertura-coverage.xml
```

### Key concepts (Khái niệm quan trọng)

- `coverage`: Regex to extract coverage % (Regex để lấy % coverage)
- `reports`: Special report types (Các loại báo cáo đặc biệt)
- `when: always`: Run even if tests fail (Chạy ngay cả khi test fail)

---

## 🔬 Lab 4: Docker Build & Push

Build and push Docker image to GitLab Container Registry.

*Build và push Docker image lên GitLab Container Registry.*

```yaml
# .gitlab-ci.yml
stages:
  - build
  - docker

variables:
  IMAGE_TAG: $CI_REGISTRY_IMAGE:$CI_COMMIT_SHORT_SHA

build-app:
  stage: build
  image: node:18-alpine
  script:
    - npm ci
    - npm run build
  artifacts:
    paths:
      - dist/

docker-build:
  stage: docker
  image: docker:24
  services:
    - docker:24-dind
  variables:
    DOCKER_TLS_CERTDIR: "/certs"
  before_script:
    - docker login -u $CI_REGISTRY_USER -p $CI_REGISTRY_PASSWORD $CI_REGISTRY
  script:
    - docker build -t $IMAGE_TAG .
    - docker push $IMAGE_TAG
    - echo "Image pushed to $IMAGE_TAG"
```

### Key concepts (Khái niệm quan trọng)

- `$CI_REGISTRY`: GitLab Container Registry URL
- `services: docker:dind`: Docker-in-Docker service
- `$CI_REGISTRY_USER/PASSWORD`: Auto-generated credentials (Credentials tự động)

---

## 🔬 Lab 5: Multi-Job Pipeline

Pipeline with multiple stages and job dependencies.

*Pipeline với nhiều stages và dependencies giữa các jobs.*

```yaml
# .gitlab-ci.yml
stages:
  - lint
  - test
  - build

lint-job:
  stage: lint
  image: node:18-alpine
  script:
    - npm ci
    - npm run lint

unit-test:
  stage: test
  image: node:18-alpine
  script:
    - npm ci
    - npm test
  needs:
    - lint-job

integration-test:
  stage: test
  image: node:18-alpine
  script:
    - npm ci
    - npm run test:integration
  needs:
    - lint-job
  allow_failure: true

build-job:
  stage: build
  image: node:18-alpine
  script:
    - npm ci
    - npm run build
  needs:
    - unit-test
  artifacts:
    paths:
      - dist/
```

### Key concepts (Khái niệm quan trọng)

- `needs`: Define job dependencies (Định nghĩa dependencies)
- `allow_failure`: Job can fail without failing pipeline (Job có thể fail mà không fail pipeline)
- Jobs in same stage run in parallel (Jobs cùng stage chạy song song)

---

## 🔬 Lab 6: Deployment Pipeline

Complete deployment pipeline with environments.

*Pipeline triển khai hoàn chỉnh với environments.*

```yaml
# .gitlab-ci.yml
stages:
  - build
  - deploy

variables:
  STAGING_SERVER: staging.example.com
  PROD_SERVER: prod.example.com

build-job:
  stage: build
  image: node:18-alpine
  script:
    - npm ci
    - npm run build
  artifacts:
    paths:
      - dist/

deploy-staging:
  stage: deploy
  image: alpine:latest
  environment:
    name: staging
    url: https://staging.example.com
  before_script:
    - apk add --no-cache openssh-client
    - eval $(ssh-agent -s)
    - echo "$SSH_PRIVATE_KEY" | ssh-add -
  script:
    - scp -r dist/* user@$STAGING_SERVER:/var/www/app/
    - echo "Deployed to staging!"
  needs:
    - build-job
  only:
    - main

deploy-production:
  stage: deploy
  image: alpine:latest
  environment:
    name: production
    url: https://example.com
  before_script:
    - apk add --no-cache openssh-client
    - eval $(ssh-agent -s)
    - echo "$SSH_PRIVATE_KEY" | ssh-add -
  script:
    - scp -r dist/* user@$PROD_SERVER:/var/www/app/
    - echo "Deployed to production!"
  needs:
    - deploy-staging
  when: manual
  only:
    - main
```

### Key concepts (Khái niệm quan trọng)

- `environment`: Define deployment environment (Định nghĩa môi trường)
- `when: manual`: Require manual trigger (Yêu cầu trigger thủ công)
- `only: main`: Only run on main branch (Chỉ chạy trên branch main)

---

## ✅ Lab Checklist (Danh sách bài lab)

- [ ] Lab 1: First Pipeline (Pipeline đầu tiên)
- [ ] Lab 2: Build Stage (Giai đoạn Build)
- [ ] Lab 3: Testing Pipeline (Pipeline Testing)
- [ ] Lab 4: Docker Build & Push
- [ ] Lab 5: Multi-Job Pipeline
- [ ] Lab 6: Deployment Pipeline

---

## 📚 Additional Resources (Tài liệu bổ sung)

- [GitLab CI/CD Documentation](https://docs.gitlab.com/ee/ci/)
- [GitLab CI/CD Examples](https://docs.gitlab.com/ee/ci/examples/)
- [Predefined Variables](https://docs.gitlab.com/ee/ci/variables/predefined_variables.html)

---

**[← Back to README](./README.md)** | **[GitHub Actions Alternative →](./README_GITHUB_ACTIONS.md)**
