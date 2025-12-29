# 📋 Bilingual Documentation Guidelines

> Documentation standards and formatting guidelines for the DevOps Journey curriculum.
>
> *Tiêu chuẩn tài liệu và hướng dẫn định dạng cho chương trình DevOps Journey.*

---

## 📑 Table of Contents (Mục lục)

1. [Language Format](#-language-format-định-dạng-ngôn-ngữ)
2. [Navigation Section](#-navigation-section-phần-điều-hướng)
3. [Module README Template](#-module-readme-template)
4. [Common Bilingual Phrases](#-common-bilingual-phrases-các-cụm-từ-song-ngữ-phổ-biến)
5. [Files Per Module](#-files-per-module)
6. [Badges](#-badges)
7. [Related Specifications](#-related-specifications-tài-liệu-liên-quan)

---

## 🌐 Language Format (Định dạng Ngôn ngữ)

This curriculum uses **bilingual format (English-Vietnamese)**.

*Chương trình này sử dụng **định dạng song ngữ (Anh-Việt)**.*

### Rule 1: Short Comments (Chú thích ngắn)

**Format:** `English (Tiếng Việt)`

Use for:

- Code comments (Chú thích code)
- Table headers (Tiêu đề bảng)
- Brief labels (Nhãn ngắn)

**Examples:**

```bash
# Read file (Đọc file)
# Write file (Ghi file)
# Run command (Chạy lệnh)
# Install dependencies (Cài đặt thư viện)
```

```python
# GET request (Yêu cầu GET)
# Error handling (Xử lý lỗi)
# Create user (Tạo user)
```

### Rule 2: Long Sentences (Câu dài)

**Format:**

```
English sentence on first line
*Vietnamese translation in italics on second line*
```

Use for:

- Module descriptions (Mô tả module)
- Important notes (Ghi chú quan trọng)
- Closing messages (Thông điệp kết thúc)

**Example:**

```markdown
> **Understanding Networks** - The foundation for all distributed systems.
> 
> *Hiểu về mạng - Nền tảng cho mọi hệ thống phân tán.*
```

### Rule 3: Section Headings (Tiêu đề mục)

**Format:** `## English Title (Tiêu đề Tiếng Việt)`

**Standard Headings:**

```markdown
## 🎯 Learning Objectives (Mục tiêu học tập)
## 📋 Prerequisites (Điều kiện tiên quyết)
## 📚 Content (Nội dung)
## 📝 Module Files (Các file trong Module)
## 🔗 Module Navigation (Điều hướng Module)
```

### Rule 4: Table Headers (Tiêu đề bảng)

**Format:** `Header (Tiêu đề)`

**Example:**

```markdown
| File | Description (Mô tả) |
|------|---------------------|
| LABS.md | Hands-on labs (Bài thực hành) |
| QUIZ.md | Knowledge check (Kiểm tra kiến thức) |
```

---

## 🔗 Navigation Section (Phần Điều hướng)

Navigation must be:

1. ✅ **Placed at the bottom** of the document
2. ✅ **Centered** using `<div align="center">`
3. ✅ **Above** the closing message
4. ✅ Using **arrow symbols** (← →)

### Navigation Template

```markdown
---

<div align="center">

### 🔗 Module Navigation (Điều hướng Module)

| ← Previous (Trước) | Current (Hiện tại) | Next (Tiếp) → |
|:------------------:|:------------------:|:-------------:|
| [Previous Module](../path/) | **Current Module** | [Next Module](../path/) |

---

**Motivational message in English! 🎉**

*Thông điệp động viên bằng tiếng Việt!*

</div>
```

---

## 📄 Module README Template

```markdown
# 🎯 Module X.X: Module Name

[![Duration](https://img.shields.io/badge/Duration-X%20hours-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Beginner-green?style=flat-square)](.)

> **English description** - Brief explanation.
> 
> *Mô tả tiếng Việt - Giải thích ngắn gọn.*

---

## 🎯 Learning Objectives (Mục tiêu học tập)

After this module, you will (Sau module này, bạn sẽ):

- ✅ Objective 1 (Mục tiêu 1)
- ✅ Objective 2 (Mục tiêu 2)

---

## 📋 Prerequisites (Điều kiện tiên quyết)

- Requirement 1 (Yêu cầu 1)

---

## 📚 Content (Nội dung)

### 1. Section Name (Tên mục)

```code
# Comment in English (Chú thích tiếng Việt)
code here
```

---

## 📝 Module Files (Các file trong Module)

| File | Description (Mô tả) |
|------|---------------------|
| [LABS.md](./LABS.md) | Hands-on labs (Bài thực hành) |
| [QUIZ.md](./QUIZ.md) | Knowledge check (Kiểm tra kiến thức) |
| [EXERCISES.md](./EXERCISES.md) | Exercises (Bài tập) |
| [PROJECT.md](./PROJECT.md) | Mini project (Dự án nhỏ) |
| [SOLUTIONS.md](./SOLUTIONS.md) | Solutions (Đáp án) |
| [CHEATSHEET.md](./CHEATSHEET.md) | Quick reference (Tra cứu nhanh) |

---

<div align="center">

### 🔗 Module Navigation (Điều hướng Module)

| ← Previous (Trước) | Current (Hiện tại) | Next (Tiếp) → |
|:------------------:|:------------------:|:-------------:|
| [X.X Previous](../path/) | **X.X Current** | [X.X Next](../path/) |

---

**Motivational message! 🚀**

*Thông điệp tiếng Việt!*

</div>
```

---

## � Common Bilingual Phrases (Các cụm từ song ngữ phổ biến)

### Headers & Titles

| English | Vietnamese |
|---------|------------|
| Learning Objectives | Mục tiêu học tập |
| Prerequisites | Điều kiện tiên quyết |
| Content | Nội dung |
| Module Files | Các file trong Module |
| Module Navigation | Điều hướng Module |
| Previous | Trước |
| Current | Hiện tại |
| Next | Tiếp |
| Description | Mô tả |

### File Types

| English | Vietnamese |
|---------|------------|
| Hands-on labs | Bài thực hành |
| Knowledge check | Kiểm tra kiến thức |
| Exercises | Bài tập |
| Solutions | Đáp án |
| Mini project | Dự án nhỏ |
| Quick reference | Tra cứu nhanh |
| Cheatsheet | Bảng tra cứu |

### Common Actions

| English | Vietnamese |
|---------|------------|
| Read file | Đọc file |
| Write file | Ghi file |
| Run command | Chạy lệnh |
| Install | Cài đặt |
| Create | Tạo |
| Update | Cập nhật |
| Delete | Xóa |
| Build | Build |
| Deploy | Deploy |
| Test | Kiểm thử |

### Module Outcomes

| English | Vietnamese |
|---------|------------|
| After this module, you will | Sau module này, bạn sẽ |
| Understand | Hiểu |
| Master | Thành thạo |
| Implement | Triển khai |
| Configure | Cấu hình |
| Work with | Làm việc với |
| Learn | Tìm hiểu |

### Closing Messages

| English | Vietnamese |
|---------|------------|
| Good luck! | Chúc may mắn! |
| Master the fundamentals! | Thành thạo kiến thức nền tảng! |
| Ready to automate! | Sẵn sàng tự động hóa! |
| Level up your skills! | Nâng cấp kỹ năng! |
| Congratulations! | Chúc mừng! |

---

## �📁 Files Per Module

Each module should contain:

| File | Purpose (Mục đích) | Required |
|------|---------------------|----------|
| README.md | Main content (Nội dung chính) | ✅ Yes |
| LABS.md | Hands-on exercises (Bài thực hành) | ✅ Yes |
| QUIZ.md | Knowledge check (Kiểm tra) | ✅ Yes |
| EXERCISES.md | Practice problems (Bài tập) | ✅ Yes |
| PROJECT.md | Mini project (Dự án nhỏ) | ✅ Yes |
| SOLUTIONS.md | Answers (Đáp án) | ✅ Yes |
| CHEATSHEET.md | Quick reference (Tra cứu nhanh) | ⭐ Recommended |

---

## 🎨 Badges

Use shields.io badges for module info:

### Duration Badges

```markdown
[![Duration](https://img.shields.io/badge/Duration-4--6%20hours-blue?style=flat-square)](.)
[![Duration](https://img.shields.io/badge/Duration-8--10%20hours-blue?style=flat-square)](.)
[![Duration](https://img.shields.io/badge/Duration-1%20week-blue?style=flat-square)](.)
[![Duration](https://img.shields.io/badge/Duration-1--2%20weeks-blue?style=flat-square)](.)
[![Duration](https://img.shields.io/badge/Duration-Ongoing-blue?style=flat-square)](.)
```

### Level Badges

```markdown
[![Level](https://img.shields.io/badge/Level-Beginner-green?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Intermediate-orange?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Advanced-red?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-All%20Levels-green?style=flat-square)](.)
```

---

## � Related Specifications (Tài liệu liên quan)

| File | Description |
|------|-------------|
| [00_MASTER_INDEX.md](./00_MASTER_INDEX.md) | Main index of all specs |
| [01_CONTENT_STANDARDS.md](./01_CONTENT_STANDARDS.md) | Content writing standards |
| [02_STYLE_GUIDE.md](./02_STYLE_GUIDE.md) | Markdown style guide |
| [10_README_DESIGN.md](./10_README_DESIGN.md) | README structure template |
| [12_LABS_DESIGN.md](./12_LABS_DESIGN.md) | Labs file template |
| [13_QUIZ_DESIGN.md](./13_QUIZ_DESIGN.md) | Quiz file template |

---

## 📅 Version History (Lịch sử phiên bản)

| Date | Version | Changes |
|------|---------|---------|
| 2025-12-29 | 1.0 | Initial bilingual guidelines |
| 2025-12-29 | 1.1 | Added common phrases table |

---

<div align="center">

**Follow these guidelines for consistent documentation! 📋**

*Tuân thủ các hướng dẫn này để có tài liệu nhất quán!*

</div>
