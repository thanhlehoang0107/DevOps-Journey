# ❓ Quiz: Git & GitLab

> 20 câu hỏi về Git.

---

### Q1: Git Init

`git init` làm gì?

- a) Clone repository
- b) Tạo mới repository
- c) Delete repository
- d) Update repository  

---

### Q2: Staging Area

Lệnh nào add file vào staging area?

- a) `git commit`
- b) `git add`
- c) `git push`
- d) `git stage`  

---

### Q3: Commit

Lệnh nào tạo commit?

- a) `git add -m "message"`
- b) `git commit -m "message"`
- c) `git push -m "message"`
- d) `git save -m "message"`  

---

### Q4: Branching

Lệnh nào tạo và switch branch?

- a) `git branch new-branch`
- b) `git checkout new-branch`
- c) `git checkout -b new-branch`
- d) `git switch new-branch`  

---

### Q5: Merge

Để merge branch `feature` vào `main`:

- a) `git checkout feature && git merge main`
- b) `git checkout main && git merge feature`
- c) `git merge main feature`
- d) `git merge feature main`  

---

### Q6: Remote

Lệnh xem remote repositories?

- a) `git remote -v`
- b) `git remote list`
- c) `git show remote`
- d) `git list remote`  

---

### Q7: Pull vs Fetch

`git pull` khác `git fetch` như thế nào?

- a) Pull chỉ download, fetch còn merge
- b) Fetch chỉ download, pull còn merge
- c) Không khác nhau
- d) Fetch dùng cho tags  

---

### Q8: Revert

Lệnh nào tạo commit mới để undo commit trước?

- a) `git reset`
- b) `git revert`
- c) `git undo`
- d) `git checkout`  

---

### Q9: Stash

`git stash` dùng để làm gì?

- a) Delete changes (Xóa thay đổi)
- b) Commit changes (Commit thay đổi)
- c) Temporarily save changes (Lưu tạm thời thay đổi)
- d) Push changes (Đẩy thay đổi)  

---

### Q10: Log

Lệnh xem commit history ngắn gọn?

- a) `git log -1`
- b) `git log --oneline`
- c) `git log --short`
- d) `git history`  

---

### Q11: Reset

`git reset --hard HEAD~1` làm gì?

- a) Xóa commit cuối, giữ changes
- b) Xóa commit cuối, xóa changes
- c) Xóa 2 commits cuối
- d) Không làm gì  

---

### Q12: Cherry-pick

`git cherry-pick` dùng để?

- a) Xóa commit
- b) Apply specific commit từ branch khác (Áp dụng commit cụ thể từ branch khác)
- c) Create branch
- d) Merge branches  

---

### Q13: Rebase

`git rebase` khác `git merge` như thế nào?

- a) Rebase tạo merge commit
- b) Rebase rewrite history, merge không (Rebase viết lại lịch sử, merge thì không)
- c) Không khác nhau
- d) Merge rewrite history  

---

### Q14: .gitignore

File nào không bị track nếu có `.gitignore` chứa `*.log`?

- a) debug.log
- b) app.log
- c) logs/error.log
- d) Tất cả  

---

### Q15: Tag

Lệnh tạo annotated tag?

- a) `git tag v1.0`
- b) `git tag -a v1.0 -m "Release"`
- c) `git tag --annotated v1.0`
- d) `git create-tag v1.0`  

---

### Q16: Diff

`git diff --staged` hiển thị gì?

- a) Changes not staged (Các thay đổi chưa stage)
- b) Changes staged but not committed (Các thay đổi đã stage nhưng chưa commit)
- c) All changes (Tất cả thay đổi)
- d) Committed changes (Các thay đổi đã commit)  

---

### Q17: Clone

`git clone --depth 1` làm gì?

- a) Clone tất cả history
- b) Clone chỉ latest commit (shallow)
- c) Clone branch specific
- d) Clone without files  

---

### Q18: Blame

`git blame file.txt` hiển thị gì?

- a) Who modified each line (Ai đã sửa từng dòng)
- b) File history (Lịch sử file)
- c) Diff
- d) Errors (Lỗi)  

---

### Q19: Submodule

Git submodule dùng để?

- a) Delete repositories
- b) Include other repos as subdirectory (Bao gồm repo khác như thư mục con)
- c) Create branches
- d) Merge repos  

---

### Q20: Hook

Pre-commit hook chạy khi nào?

- a) Before push (Trước khi push)
- b) Before commit is created (Trước khi commit được tạo)
- c) After commit (Sau khi commit)
- d) After push (Sau khi push)  

---

## 📝 Answers

<details>
<summary>Click để xem đáp án</summary>

| Q | A | Q | A |
|---|---|---|---|
| 1 | b | 11 | b |
| 2 | b | 12 | b |
| 3 | b | 13 | b |
| 4 | c | 14 | d |
| 5 | b | 15 | b |
| 6 | a | 16 | b |
| 7 | b | 17 | b |
| 8 | b | 18 | a |
| 9 | c | 19 | b |
| 10 | b | 20 | b |

</details>

---

**[← Back to README](./README.md)**
