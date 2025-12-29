# 🎯 Project: Git & GitHub

> Mini project: **Team Collaboration Simulation**

---

## 📋 Project Overview

### Project Name: **Git Workflow Implementation**

Simulate team development workflow với Git.

### Duration: 2 ngày

---

## 🎯 Requirements

### Scenario

Bạn là DevOps lead, setup Git workflow cho team 3 người.

### Tasks

#### 1. Repository Setup

- Create repository với proper structure
- Setup branch protection rules
- Create CONTRIBUTING.md
- Setup PR template

#### 2. Implement Git Flow

```
main ────────────────────────────────
  │
  └── develop ───────────────────────
        │
        ├── feature/user-auth ──────
        │
        ├── feature/api-endpoints ──
        │
        └── release/1.0.0 ──────────
```

#### 3. Collaboration Features

- Create and review PRs
- Handle merge conflicts
- Use conventional commits
- Create releases với tags

#### 4. Automation

- Setup commit hooks
- Create GitHub Actions for CI
- Automate changelog generation

---

## 📁 Project Structure

```
team-project/
├── .github/
│   ├── workflows/
│   │   └── ci.yml
│   ├── PULL_REQUEST_TEMPLATE.md
│   └── ISSUE_TEMPLATE/
├── src/
├── tests/
├── docs/
│   └── git-workflow.md
├── .gitignore
├── .gitattributes
├── CONTRIBUTING.md
├── CHANGELOG.md
└── README.md
```

---

## ✅ Deliverables

- [ ] Repository với complete setup
- [ ] Branch protection configured
- [ ] 3+ merged PRs
- [ ] Release v1.0.0 với tag
- [ ] CI workflow running
- [ ] Documentation complete

---

**Good luck! 🚀**
