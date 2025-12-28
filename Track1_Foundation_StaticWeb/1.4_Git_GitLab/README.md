# 📦 Module 1.4: Git & GitHub

> Version Control - Quản lý code và cộng tác hiệu quả

---

## 📋 Thông tin Module

| Thuộc tính | Giá trị |
|------------|---------|
| **Thời lượng** | 8-10 giờ |
| **Độ khó** | ⭐ Beginner |
| **Yêu cầu trước** | Module 1.3 hoàn thành |

---

## 🎯 Mục tiêu học tập

- [ ] Hiểu Git là gì và tại sao cần dùng
- [ ] Thao tác cơ bản: init, add, commit, push, pull
- [ ] Branching và merging
- [ ] Xử lý conflicts
- [ ] Làm việc với GitHub/GitLab

---

## 📖 Nội dung

### 1. Git là gì?

**Git** = Distributed Version Control System (DVCS)

```
┌─────────────────────────────────────────────────────────────┐
│                    GIT WORKFLOW                              │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  Working      Staging       Local         Remote            │
│  Directory    Area          Repository    Repository        │
│                                                              │
│    Files   →  git add   →  git commit  →  git push   →     │
│  (modified)   (staged)     (committed)   (pushed)  GitHub  │
│                                                              │
│              ←  git restore --staged                         │
│    ←─────────────────────────  git pull  ←─────────────     │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

---

### 2. Cấu hình Git

```bash
# Cấu hình user (bắt buộc)
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Kiểm tra cấu hình
git config --list

# Cấu hình editor (optional)
git config --global core.editor "code --wait"

# Line endings
git config --global core.autocrlf true   # Windows
git config --global core.autocrlf input  # Linux/macOS
```

---

### 3. Các lệnh cơ bản

#### Khởi tạo Repository

```bash
# Tạo repo mới
git init

# Clone repo từ remote
git clone https://github.com/user/repo.git
git clone git@github.com:user/repo.git
```

#### Workflow cơ bản

```bash
# Xem trạng thái
git status

# Stage files
git add file.txt          # Một file
git add .                 # Tất cả files

# Commit
git commit -m "Add feature X"

# Push lên remote
git push origin main

# Pull từ remote
git pull origin main
```

#### Xem lịch sử

```bash
git log                   # Full log
git log --oneline         # Compact
git log --oneline -10     # 10 commits gần nhất
git log --graph           # Với graph
```

---

### 4. Branching

```
main      ─────●─────●─────●─────────●─────►
               │                     ▲
               │     ┌──────●─────●──┘
               │     │   feature branch
               └─────┘
```

#### Làm việc với branches

```bash
# Xem branches
git branch              # Local
git branch -a           # Local + Remote

# Tạo branch mới
git branch feature-x

# Chuyển branch
git checkout feature-x
git switch feature-x    # Modern syntax

# Tạo và chuyển (1 lệnh)
git checkout -b feature-x
git switch -c feature-x

# Xóa branch
git branch -d feature-x   # Đã merge
git branch -D feature-x   # Force delete
```

#### Merge

```bash
# Đứng ở main, merge feature vào
git checkout main
git merge feature-x

# Merge với commit message
git merge feature-x -m "Merge feature-x into main"
```

---

### 5. Git Workflow phổ biến

#### Feature Branch Workflow

```bash
# 1. Cập nhật main
git checkout main
git pull origin main

# 2. Tạo feature branch
git checkout -b feature/login-page

# 3. Làm việc, commit
git add .
git commit -m "Add login form"
git commit -m "Add validation"

# 4. Push branch
git push origin feature/login-page

# 5. Tạo Pull Request trên GitHub

# 6. Sau khi merge, xóa branch
git checkout main
git pull origin main
git branch -d feature/login-page
```

---

### 6. Xử lý Conflicts

```bash
# Khi merge hoặc pull có conflict
<<<<<<< HEAD
code từ branch hiện tại
=======
code từ branch khác
>>>>>>> feature-x

# Giải quyết:
# 1. Sửa file, xóa conflict markers
# 2. git add file-đã-fix
# 3. git commit
```

---

### 7. Undo Changes

```bash
# Unstage file
git restore --staged file.txt

# Discard changes (chưa commit)
git restore file.txt

# Undo last commit (giữ changes)
git reset --soft HEAD~1

# Undo last commit (xóa changes) - NGUY HIỂM!
git reset --hard HEAD~1

# Revert commit (tạo commit ngược)
git revert abc1234
```

---

### 8. .gitignore

```bash
# File: .gitignore

# Dependencies
node_modules/
vendor/
venv/

# Build outputs
dist/
build/
*.pyc

# IDE
.vscode/
.idea/

# Secrets
.env
*.key
secrets/

# OS files
.DS_Store
Thumbs.db

# Logs
*.log
logs/
```

---

### 9. SSH Keys cho GitHub

```bash
# Tạo SSH key
ssh-keygen -t ed25519 -C "your.email@example.com"

# Copy public key
cat ~/.ssh/id_ed25519.pub
# Paste vào GitHub → Settings → SSH Keys

# Test connection
ssh -T git@github.com
```

---

## 📁 Files trong module này

| File | Mục đích |
|------|----------|
| [CHEATSHEET.md](./CHEATSHEET.md) | Tra cứu nhanh Git |
| [LABS.md](./LABS.md) | Bài thực hành |
| [QUIZ.md](./QUIZ.md) | Kiểm tra kiến thức |
| [EXERCISES.md](./EXERCISES.md) | Bài tập |
| [PROJECT.md](./PROJECT.md) | Mini project |
| [SOLUTIONS.md](./SOLUTIONS.md) | Đáp án |

---

## 🔗 Navigation

[⬅️ 1.3 Network](../1.3_Network_Basics/README.md) | [📚 Track 1](../README.md) | [1.5 Docker ➡️](../1.5_Docker_Fundamentals/README.md)

---

*Cập nhật: 2025-12-29*
