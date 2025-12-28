# 🤝 Contributing to DevOps Journey

Cảm ơn bạn đã quan tâm đến việc đóng góp cho **DevOps Journey**! Mọi đóng góp đều được chào đón và đánh giá cao.

---

## 📋 Mục Lục

- [Code of Conduct](#-code-of-conduct)
- [Cách Đóng Góp](#-cách-đóng-góp)
- [Quy Trình Pull Request](#-quy-trình-pull-request)
- [Coding Standards](#-coding-standards)
- [Commit Convention](#-commit-convention)
- [Documentation Guidelines](#-documentation-guidelines)
- [Báo Cáo Bugs](#-báo-cáo-bugs)
- [Đề Xuất Features](#-đề-xuất-features)
- [Community](#-community)

---

## 📜 Code of Conduct

Dự án này tuân theo [Contributor Covenant Code of Conduct](https://www.contributor-covenant.org/). Bằng việc tham gia, bạn đồng ý tuân thủ các quy tắc này.

### Quy tắc cơ bản

- ✅ Tôn trọng tất cả contributors
- ✅ Đón nhận phản hồi mang tính xây dựng
- ✅ Tập trung vào điều tốt nhất cho community
- ✅ Thể hiện sự đồng cảm với người khác

---

## 🚀 Cách Đóng Góp

### Các loại đóng góp được chào đón

| Loại | Mô Tả |
|------|-------|
| 📝 **Content** | Viết/cập nhật nội dung module |
| 🐛 **Bug fixes** | Sửa lỗi typo, links hỏng |
| 🔬 **Labs** | Thêm bài thực hành mới |
| ❓ **Quizzes** | Thêm câu hỏi kiểm tra |
| 🌐 **Translations** | Dịch sang ngôn ngữ khác |
| 🖼️ **Diagrams** | Thêm hình ảnh minh họa |
| 📖 **Documentation** | Cải thiện documentation |

### Quick Start

```bash
# 1. Fork repository
# Click "Fork" button trên GitHub

# 2. Clone your fork
git clone https://github.com/YOUR_USERNAME/DevOps-Journey.git
cd DevOps-Journey

# 3. Add upstream remote
git remote add upstream https://github.com/thanhlehoang0107/DevOps-Journey.git

# 4. Create a branch
git checkout -b feature/your-feature-name

# 5. Make your changes
# ... edit files ...

# 6. Commit changes
git add .
git commit -m "feat: add new lab for Docker module"

# 7. Push to your fork
git push origin feature/your-feature-name

# 8. Create Pull Request
# Go to GitHub and click "New Pull Request"
```

---

## 🔄 Quy Trình Pull Request

### Trước khi tạo PR

- [ ] Sync fork với upstream mới nhất
- [ ] Tạo branch mới từ `main`
- [ ] Test nội dung/code của bạn
- [ ] Đảm bảo không có lỗi spelling
- [ ] Cập nhật documentation nếu cần

### PR Checklist

```markdown
## Description
<!-- Mô tả ngắn gọn về thay đổi -->

## Type of Change
- [ ] 📝 Content update
- [ ] 🐛 Bug fix
- [ ] ✨ New feature
- [ ] 📖 Documentation
- [ ] 🔧 Configuration

## Testing
<!-- Bạn đã test như thế nào? -->

## Screenshots (nếu có)
<!-- Thêm screenshots nếu relevant -->

## Checklist
- [ ] Tôi đã đọc Contributing Guidelines
- [ ] Code/Content tuân theo project standards
- [ ] Không có lỗi typo
- [ ] Links hoạt động đúng
```

### Review Process

1. **Automated Checks** - GitHub Actions kiểm tra format
2. **Maintainer Review** - Review trong 2-3 ngày làm việc
3. **Feedback** - Sửa đổi nếu cần
4. **Merge** - PR được merge vào main

---

## 📏 Coding Standards

### Markdown Files

```markdown
# Heading 1 (chỉ 1 per file)

## Heading 2

### Heading 3

- Bullet points với dấu `-`
- Không trộn `-` và `*`

1. Numbered lists
2. Sử dụng đúng thứ tự

`inline code` cho commands ngắn

​```bash
# Code blocks cho multi-line
docker run -d nginx
​```

| Column 1 | Column 2 |
|----------|----------|
| Data     | Data     |
```

### File Naming

```
✅ Good:
README.md
LABS.md
docker-compose.yml
my_script.sh

❌ Bad:
readme.MD
Labs.Md
Docker Compose.yml
my script.sh
```

### Images

- Đặt trong folder `images/` của module
- Sử dụng format `.png` hoặc `.webp`
- Tên file lowercase với dashes: `docker-architecture.png`
- Resize images hợp lý (max 1200px width)

---

## 💬 Commit Convention

Sử dụng [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>(<scope>): <description>

[optional body]

[optional footer]
```

### Types

| Type | Mô Tả |
|------|-------|
| `feat` | Thêm feature/content mới |
| `fix` | Sửa bug/lỗi |
| `docs` | Thay đổi documentation |
| `style` | Formatting, không thay đổi code |
| `refactor` | Restructure, không thay đổi behavior |
| `test` | Thêm/sửa tests |
| `chore` | Maintenance tasks |

### Examples

```bash
# Good commits
git commit -m "feat(track1): add Docker networking lab"
git commit -m "fix(track2): correct typo in Kubernetes guide"
git commit -m "docs: update README with new badge"
git commit -m "chore: update .gitignore"

# Bad commits
git commit -m "update"
git commit -m "fix stuff"
git commit -m "WIP"
```

---

## 📖 Documentation Guidelines

### README.md Structure

Mỗi module README nên có:

```markdown
# Module Title

> Brief description

---

## 🎯 Learning Objectives
- Objective 1
- Objective 2

---

## 📋 Prerequisites
- Prerequisite 1

---

## 📚 Content

### Topic 1
...

### Topic 2
...

---

## 🔗 Related Resources
- [Link 1](url)
- [Link 2](url)

---

## ➡️ Next Steps
- Link to next module
```

### LABS.md Structure

```markdown
# Labs: Module Name

## Lab 1: Lab Title

### Objectives
- What students will learn

### Prerequisites
- What's needed before starting

### Steps

#### Step 1: Title
​```bash
command here
​```

Expected output:
​```
output here
​```

#### Step 2: Title
...

### Verification
How to verify the lab is complete

### Cleanup
​```bash
# Commands to clean up resources
​```

---

## Lab 2: Next Lab Title
...
```

---

## 🐛 Báo Cáo Bugs

### Tạo Bug Report

1. **Check existing issues** - Xem bug đã được report chưa
2. **Create new issue** với template:

```markdown
## Bug Description
<!-- Mô tả rõ ràng bug -->

## Steps to Reproduce
1. Go to '...'
2. Click on '....'
3. See error

## Expected Behavior
<!-- Bạn mong đợi điều gì xảy ra -->

## Actual Behavior
<!-- Điều gì thực sự xảy ra -->

## Screenshots
<!-- Nếu có -->

## Environment
- OS: [e.g. Windows 11]
- Browser: [e.g. Chrome 120]
- Tool version: [e.g. Docker 24.0]

## Additional Context
<!-- Thông tin thêm -->
```

---

## 💡 Đề Xuất Features

### Tạo Feature Request

```markdown
## Feature Description
<!-- Mô tả feature bạn muốn -->

## Problem it Solves
<!-- Vấn đề này giải quyết điều gì? -->

## Proposed Solution
<!-- Bạn đề xuất giải pháp như thế nào? -->

## Alternatives Considered
<!-- Các phương án khác bạn đã cân nhắc -->

## Additional Context
<!-- Hình ảnh, links, ví dụ... -->
```

---

## 🏷️ Labels

| Label | Mô Tả |
|-------|-------|
| `good first issue` | Phù hợp cho người mới |
| `help wanted` | Cần người hỗ trợ |
| `bug` | Lỗi cần sửa |
| `enhancement` | Feature request |
| `documentation` | Liên quan đến docs |
| `track-1` ... `track-5` | Specific track |

---

## 👥 Community

### Maintainers

- **Thanh Le Hoang** - [@thanhlehoang0107](https://github.com/thanhlehoang0107)

### Contributors

<!-- Contributors sẽ được liệt kê tự động -->

Cảm ơn tất cả những người đã đóng góp! 🙏

---

## ❓ Questions?

Nếu bạn có câu hỏi:

1. Check [existing issues](https://github.com/thanhlehoang0107/DevOps-Journey/issues)
2. Tạo issue mới với label `question`
3. Email: <thanhlehoang0107@gmail.com>

---

<div align="center">

**Cảm ơn bạn đã đóng góp cho DevOps Journey! 🚀**

</div>
