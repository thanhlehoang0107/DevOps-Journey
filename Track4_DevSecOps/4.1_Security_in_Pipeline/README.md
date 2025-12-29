# 🔐 Module 4.1: Security in Pipeline

[![Duration](https://img.shields.io/badge/Duration-1%20week-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Intermediate-orange?style=flat-square)](.)

> **Shift-Left Security** - Integrate security into CI/CD pipeline.
>
> *Bảo mật Shift-Left - Tích hợp bảo mật vào CI/CD pipeline.*

---

## 🎯 Learning Objectives (Mục tiêu học tập)

After this module, you will (Sau module này, bạn sẽ):

- ✅ Implement SAST - Static Application Security Testing (Triển khai SAST)
- ✅ Use DAST - Dynamic Application Security Testing (Sử dụng DAST)
- ✅ Perform SCA - Software Composition Analysis (Thực hiện SCA)
- ✅ Configure secret scanning (Cấu hình quét secrets)
- ✅ Secure containers (Bảo mật container)
- ✅ Apply Policy as Code (Áp dụng Policy as Code)

---

## 📚 Content (Nội dung)

### 1. SAST Tools (Công cụ SAST)

```yaml
# GitHub Actions - CodeQL
- name: CodeQL Analysis
  uses: github/codeql-action/analyze@v2

# SonarQube
sonar-scanner \
  -Dsonar.projectKey=myproject \
  -Dsonar.sources=. \
  -Dsonar.host.url=http://sonarqube:9000
```

### 2. Dependency Scanning (Quét dependencies)

```bash
# npm audit (Kiểm tra npm)
npm audit

# Snyk
snyk test

# OWASP Dependency Check
dependency-check --project myapp --scan ./
```

### 3. Secret Scanning (Quét secrets)

```yaml
# Gitleaks
- name: Scan for secrets (Quét secrets)
  uses: gitleaks/gitleaks-action@v2

# TruffleHog
trufflehog git https://github.com/user/repo
```

### 4. Container Scanning (Quét container)

```bash
# Trivy
trivy image myapp:latest

# Docker Scout
docker scout cves myapp:latest
```

### 5. Policy as Code (OPA)

```rego
# policy.rego
package kubernetes.admission

deny[msg] {
    input.request.kind.kind == "Pod"
    not input.request.object.spec.securityContext.runAsNonRoot
    msg := "Pods must run as non-root"
}
```

---

## 📝 Module Files (Các file trong Module)

| File | Description (Mô tả) |
|------|---------------------|
| [LABS.md](./LABS.md) | Hands-on labs (Bài thực hành) |
| [QUIZ.md](./QUIZ.md) | Knowledge check (Kiểm tra kiến thức) |
| [EXERCISES.md](./EXERCISES.md) | Exercises (Bài tập) |
| [SOLUTIONS.md](./SOLUTIONS.md) | Solutions (Đáp án) |

---

<div align="center">

### 🔗 Module Navigation (Điều hướng Module)

| ← Previous (Trước) | Current (Hiện tại) | Next (Tiếp) → |
|:------------------:|:------------------:|:-------------:|
| [Track 3 Capstone](../../Track3_Cloud_Network_Design/3.7_Capstone_Project/) | **4.1 Security Pipeline** | [4.2 Infra Security](../4.2_Infra_Security/) |

---

**Secure your pipeline! 🔐**

*Bảo mật pipeline của bạn!*

</div>
