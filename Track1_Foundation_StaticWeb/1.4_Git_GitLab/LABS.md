# 🔬 Labs: Git & GitHub

> Bài thực hành Git và GitHub cho DevOps.

---

## 🔬 Lab 1: Git Setup & Basics

### Steps

```bash
# Configure Git
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
git config --global init.defaultBranch main

# Create repository
mkdir my-project && cd my-project
git init

# Create files
echo "# My Project" > README.md
echo "node_modules/" > .gitignore

# Stage and commit
git add README.md .gitignore
git commit -m "Initial commit"

# View history
git log --oneline
```

---

## 🔬 Lab 2: Branching & Merging

```bash
# Create feature branch
git checkout -b feature/add-login

# Make changes
echo "Login feature" > login.txt
git add login.txt
git commit -m "Add login feature"

# Switch to main
git checkout main

# Merge feature
git merge feature/add-login

# Delete branch
git branch -d feature/add-login
```

---

## 🔬 Lab 3: Remote Repository

```bash
# Add remote
git remote add origin https://github.com/user/repo.git

# Push
git push -u origin main

# Clone
git clone https://github.com/user/repo.git

# Fetch & Pull
git fetch origin
git pull origin main
```

---

## 🔬 Lab 4: Resolving Conflicts

```bash
# Create conflict situation
git checkout -b branch-a
echo "Content A" > file.txt
git add file.txt && git commit -m "Branch A changes"

git checkout main
echo "Content B" > file.txt
git add file.txt && git commit -m "Main changes"

# Merge (will conflict)
git merge branch-a

# Resolve manually, then:
git add file.txt
git commit -m "Resolve merge conflict"
```

---

## 🔬 Lab 5: Git Flow Workflow

```bash
# Create branches
git checkout -b develop
git checkout -b feature/user-auth

# Work on feature
git commit -m "feat: add authentication"

# Merge to develop
git checkout develop
git merge feature/user-auth

# Create release
git checkout -b release/1.0.0
git commit -m "chore: prepare release 1.0.0"

# Merge to main and develop
git checkout main
git merge release/1.0.0
git tag v1.0.0
```

---

## 🔬 Lab 6: Git Hooks

```bash
# Create pre-commit hook
cat << 'EOF' > .git/hooks/pre-commit
#!/bin/bash
echo "Running pre-commit checks..."

# Check for debug statements
if grep -r "console.log\|print(" --include="*.js" --include="*.py" .; then
    echo "Error: Debug statements found!"
    exit 1
fi

echo "Pre-commit checks passed!"
EOF

chmod +x .git/hooks/pre-commit
```

---

## ✅ Checklist

- [ ] Lab 1: Git Setup
- [ ] Lab 2: Branching
- [ ] Lab 3: Remote
- [ ] Lab 4: Conflicts
- [ ] Lab 5: Git Flow
- [ ] Lab 6: Hooks

---

**[← Back to README](./README.md)**
