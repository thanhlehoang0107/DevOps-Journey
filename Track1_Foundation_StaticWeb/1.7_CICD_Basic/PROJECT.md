# 🎯 Project: CI/CD Basic

> Mini project: **Complete CI/CD Pipeline**

---

## 📋 Project Overview

### Project Name: **Full CI/CD Pipeline Implementation**

Xây dựng complete CI/CD pipeline với GitHub Actions.

### Duration: 2-3 ngày

---

## 🎯 Requirements

### Pipeline Stages

```
┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐
│  Lint   │ -> │  Test   │ -> │  Build  │ -> │ Deploy  │
└─────────┘    └─────────┘    └─────────┘    └─────────┘
```

### Features

#### 1. Code Quality

- Linting (ESLint/Prettier)
- Code formatting check
- Security scanning

#### 2. Testing

- Unit tests
- Integration tests
- Coverage report
- Test result artifacts

#### 3. Build

- Docker image build
- Multi-platform build
- Image scanning
- Push to registry

#### 4. Deployment

- Deploy to staging (auto)
- Deploy to production (manual approval)
- Rollback capability
- Deployment notifications

---

## 📁 Project Structure

```
cicd-project/
├── .github/
│   ├── workflows/
│   │   ├── ci.yml
│   │   ├── cd.yml
│   │   └── security.yml
│   ├── CODEOWNERS
│   └── dependabot.yml
├── src/
├── tests/
├── Dockerfile
├── docker-compose.yml
└── README.md
```

---

## 📊 Expected Workflows

### ci.yml

```yaml
name: CI
on: [push, pull_request]

jobs:
  lint:
    # ...
  test:
    needs: lint
    # ...
  build:
    needs: test
    # ...
```

### cd.yml

```yaml
name: CD
on:
  push:
    branches: [main]

jobs:
  deploy-staging:
    # Auto deploy
  deploy-production:
    needs: deploy-staging
    environment: production
    # Manual approval
```

---

## ✅ Deliverables

- [ ] CI workflow (lint, test, build)
- [ ] CD workflow (staging, production)
- [ ] Docker build & push
- [ ] Environment protection rules
- [ ] Secrets properly configured
- [ ] Status badges in README
- [ ] Documentation

---

## 📊 Evaluation

| Criteria | Points |
|----------|--------|
| CI Pipeline working | 30 |
| CD Pipeline working | 30 |
| Docker integration | 15 |
| Security measures | 15 |
| Documentation | 10 |

---

**Good luck! 🚀**
