# 🔐 Module 4.1: Security in Pipeline

> **Shift-Left Security** - Tích hợp security vào CI/CD pipeline.

---

## 🎯 Learning Objectives

- ✅ SAST (Static Application Security Testing)
- ✅ DAST (Dynamic Application Security Testing)
- ✅ SCA (Software Composition Analysis)
- ✅ Secret scanning
- ✅ Container security
- ✅ Policy as Code

---

## 📚 Content

### 1. SAST Tools

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

### 2. Dependency Scanning

```bash
# npm audit
npm audit

# Snyk
snyk test

# OWASP Dependency Check
dependency-check --project myapp --scan ./
```

### 3. Secret Scanning

```yaml
# Gitleaks
- name: Scan for secrets
  uses: gitleaks/gitleaks-action@v2

# TruffleHog
trufflehog git https://github.com/user/repo
```

### 4. Container Scanning

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

## 📝 Module Files

- [LABS.md](./LABS.md) | [QUIZ.md](./QUIZ.md) | [EXERCISES.md](./EXERCISES.md)
