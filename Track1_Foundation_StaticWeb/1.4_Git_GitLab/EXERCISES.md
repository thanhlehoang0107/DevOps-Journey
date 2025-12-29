# 💪 Exercises: Git & GitHub

> Bài tập tự luyện Git.

---

## Exercise 1: Repository Setup ⭐

1. Tạo repository mới với README, .gitignore (Node.js), và LICENSE
2. Clone về local
3. Tạo structure:

   ```
   project/
   ├── src/
   ├── tests/
   ├── docs/
   └── .github/
   ```

4. Commit và push

---

## Exercise 2: Branching Strategy ⭐⭐

1. Tạo branches: `develop`, `feature/auth`, `feature/api`
2. Implement "features" (tạo files) trong mỗi branch
3. Merge `feature/auth` vào `develop`
4. Merge `feature/api` vào `develop`
5. Create release branch `release/1.0`
6. Merge release vào `main` và `develop`
7. Tag version `v1.0.0`

---

## Exercise 3: Conflict Resolution ⭐⭐

1. Tạo file `config.json` trên `main`
2. Tạo 2 branches từ main
3. Edit cùng dòng trên cả 2 branches
4. Merge branch 1 vào main
5. Merge branch 2 (sẽ conflict)
6. Resolve conflict manually
7. Document conflict resolution process

---

## Exercise 4: Interactive Rebase ⭐⭐⭐

1. Tạo 5 commits với messages không tốt
2. Sử dụng `git rebase -i` để:
   - Squash 2 commits
   - Reword 2 commits
   - Reorder commits
3. Push với `--force-with-lease`

---

## Exercise 5: Git Hooks ⭐⭐

Tạo hooks:

1. **pre-commit**: Check for TODO comments
2. **commit-msg**: Enforce conventional commits
3. **pre-push**: Run tests

---

## Exercise 6: Collaboration Workflow ⭐⭐⭐

1. Fork một public repository
2. Clone fork về local
3. Add upstream remote
4. Create feature branch
5. Make changes và commit
6. Sync với upstream
7. Create Pull Request

---

## 📝 Checklist

- [ ] Exercise 1: Repository Setup
- [ ] Exercise 2: Branching Strategy
- [ ] Exercise 3: Conflict Resolution
- [ ] Exercise 4: Interactive Rebase
- [ ] Exercise 5: Git Hooks
- [ ] Exercise 6: Collaboration

---

**[← Back to README](./README.md)** | **[View Solutions →](./SOLUTIONS.md)**
