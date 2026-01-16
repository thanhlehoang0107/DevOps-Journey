# Windows Setup Guide

> 🪟 Hướng dẫn thiết lập môi trường DevOps trên Windows 10/11

---

## Track 1 Setup

### Cách 1: Tự động (Khuyến nghị)

```powershell
# Mở PowerShell với quyền Administrator
Set-ExecutionPolicy Bypass -Scope Process -Force
.\scripts\windows\setup_track1.ps1
```

### Cách 2: Thủ công

#### Bước 1: Cài đặt WSL2

1. Mở PowerShell với quyền Administrator
2. Chạy lệnh:

   ```powershell
   wsl --install
   ```

3. Khởi động lại máy tính

#### Bước 2: Cài đặt Docker Desktop

1. Tải từ [Docker Desktop](https://www.docker.com/products/docker-desktop/)
2. Chạy installer
3. Khởi động Docker Desktop

#### Bước 3: Cài đặt Git

1. Tải từ [Git SCM](https://git-scm.com/download/win)
2. Chạy installer với default options

#### Bước 4: Cài đặt VS Code

1. Tải từ [VS Code](https://code.visualstudio.com/)
2. Cài đặt extensions: Docker, Remote WSL

### Verify Track 1

```powershell
.\scripts\windows\verify_track1.ps1
```

---

## Track 2 Setup

*(Nội dung sẽ được bổ sung)*

---

## Track 3 Setup

*(Nội dung sẽ được bổ sung)*

---

## Track 4 Setup

*(Nội dung sẽ được bổ sung)*

---

## 🔗 Navigation

[⬅️ README](./README.md) | [macOS Setup ➡️](./MACOS_SETUP.md)
