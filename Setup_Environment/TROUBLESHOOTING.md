# Troubleshooting - Xử Lý Lỗi Phổ Biến

---

## Docker Issues

### Docker daemon not running

**Lỗi:**

```
Cannot connect to the Docker daemon
```

**Giải pháp:**

- Windows: Mở Docker Desktop
- Linux: `sudo systemctl start docker`

### Permission denied

**Lỗi:**

```
permission denied while trying to connect to the Docker daemon socket
```

**Giải pháp:**

```bash
sudo usermod -aG docker $USER
# Logout và login lại
```

---

## WSL2 Issues (Windows)

### WSL2 chưa được enable

**Giải pháp:**

```powershell
wsl --install
# Restart máy
```

---

## Git Issues

### Git không nhận credentials

**Giải pháp:**

```bash
git config --global credential.helper store
```

---

## 🔗 Navigation

[⬅️ Tools Overview](./TOOLS_OVERVIEW.md) | [README ➡️](./README.md)
