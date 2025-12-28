# Setup Environment - Thiết Lập Môi Trường

> 🛠️ Module này hướng dẫn thiết lập môi trường học tập cho toàn bộ khóa học DevOps Journey.

---

## 📋 Giới thiệu

Trước khi bắt đầu học DevOps, bạn cần thiết lập môi trường phát triển phù hợp. Module này cung cấp:

- **Hướng dẫn chi tiết** cho từng hệ điều hành
- **Scripts tự động** để cài đặt nhanh
- **File verify** để kiểm tra môi trường đã sẵn sàng

---

## 🖥️ Bạn đang dùng hệ điều hành nào?

| Hệ điều hành | Hướng dẫn | Script tự động |
|--------------|-----------|----------------|
| Windows 10/11 | [WINDOWS_SETUP.md](./WINDOWS_SETUP.md) | `scripts/windows/` |
| macOS | [MACOS_SETUP.md](./MACOS_SETUP.md) | `scripts/macos/` |
| Linux (Ubuntu/Debian) | [LINUX_SETUP.md](./LINUX_SETUP.md) | `scripts/linux/` |

---

## 📚 Bạn đang học Track nào?

| Track | Tools cần cài | Verify script |
|-------|---------------|---------------|
| Track 1 | Git, Docker, VS Code, NGINX | `verify_track1.sh/ps1` |
| Track 2 | + Jenkins, kubectl, Helm | `verify_track2.sh/ps1` |
| Track 3 | + Terraform, AWS CLI | `verify_track3.sh/ps1` |
| Track 4 | + Trivy, OWASP tools | `verify_track4.sh/ps1` |

---

## 📁 Cấu trúc thư mục

```
Setup_Environment/
├── images/                    # Screenshots hướng dẫn
├── scripts/                   # Scripts tự động
│   ├── windows/
│   ├── macos/
│   └── linux/
├── README.md                  # File này
├── WINDOWS_SETUP.md           # Hướng dẫn Windows
├── MACOS_SETUP.md             # Hướng dẫn macOS
├── LINUX_SETUP.md             # Hướng dẫn Linux
├── TOOLS_OVERVIEW.md          # Tổng quan tools
├── TROUBLESHOOTING.md         # Xử lý lỗi
├── CHEATSHEET.md              # Tra cứu nhanh
└── QUIZ.md                    # Kiểm tra kiến thức
```

---

## 🔗 Navigation

[📚 Mục lục chính](../README.md) | [Track 1 ➡️](../Track1_Foundation_StaticWeb/README.md)

---

*Cập nhật: 2025-12-28*
