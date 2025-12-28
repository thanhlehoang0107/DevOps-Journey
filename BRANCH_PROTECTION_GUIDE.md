# 🔒 Hướng Dẫn Thiết Lập Branch Protection trên GitHub

> Hướng dẫn chi tiết để bảo vệ nhánh `main` - ngăn không cho merge/push trực tiếp từ nhánh `Design`.

---

## 📋 Tổng quan

Sau khi thiết lập Branch Protection Rules:

- ❌ **Không ai** có thể push trực tiếp lên `main`
- ❌ **Không ai** có thể merge PR mà không có approval
- ✅ Chỉ có thể merge qua **Pull Request được duyệt**

---

## 📝 Các bước thực hiện

### Bước 1: Truy cập Settings của Repository

1. Mở trình duyệt và truy cập:

   **<https://github.com/thanhlehoang0107/DevOps-Journey>**

2. Click vào tab **"Settings"** (góc phải phía trên)

![Repository Page](./images/step1_settings.png)

---

### Bước 2: Vào mục Branches

1. Trong menu bên trái, chọn **"Branches"**

   Hoặc truy cập trực tiếp:

   **<https://github.com/thanhlehoang0107/DevOps-Journey/settings/branches>**

![Branches Settings](./images/step2_branches.png)

---

### Bước 3: Thêm Branch Protection Rule

1. Click nút **"Add branch protection rule"** hoặc **"Add rule"**

![Add Rule](./images/step3_add_rule.png)

---

### Bước 4: Cấu hình Protection Rule cho nhánh `main`

Điền các thông tin sau:

#### 4.1 Branch name pattern

```
main
```

#### 4.2 Protect matching branches

Tích chọn các options sau:

| Option | Mô tả |
|--------|-------|
| ✅ **Require a pull request before merging** | Bắt buộc tạo PR để merge |
| ✅ **Require approvals** | Yêu cầu số lượng approvals (đặt = 1 hoặc nhiều hơn) |
| ✅ **Dismiss stale pull request approvals when new commits are pushed** | Hủy approval nếu có commit mới |
| ✅ **Require status checks to pass before merging** | (Tùy chọn - nếu có CI/CD) |
| ✅ **Require conversation resolution before merging** | Bắt buộc resolve tất cả comments |
| ✅ **Do not allow bypassing the above settings** | Ngăn cả admin bypass |

![Configure Rule](./images/step4_configure.png)

---

### Bước 5: Lưu Rule

1. Scroll xuống cuối trang
2. Click nút **"Create"** hoặc **"Save changes"**

![Save Rule](./images/step5_save.png)

---

## ✅ Kết quả

Sau khi thiết lập xong:

1. **Nhánh `main`** sẽ có biểu tượng 🔒 (Protected)
2. Khi ai đó cố gắng push trực tiếp lên `main`:

   ```
   remote: error: GH006: Protected branch update failed
   ```

3. Để đưa code vào `main`, họ phải:
   - Tạo Pull Request từ branch khác
   - Chờ được approve bởi reviewer
   - Merge qua GitHub UI

---

## 🎯 Kết quả mong đợi

```
+-------------------+     +-----------------+
|   Design branch   |     |   main branch   |
|   (Full content)  | --> |   (Protected)   |
+-------------------+     +-----------------+
         |                        ↑
         |                        | (Chỉ qua PR được approve)
         +------------------------+
```

---

## ❓ FAQ

**Q: Nếu tôi là owner, tôi có thể bypass không?**
A: Có thể, trừ khi bạn tích chọn "Do not allow bypassing the above settings"

**Q: Làm sao để merge từ Design sang main?**
A: Tạo Pull Request từ `Design` → `main`, chờ approve, rồi merge.

**Q: Ai có thể approve PR?**
A: Collaborators với quyền Write hoặc Admin.

---

*Cập nhật: 2025-12-29*
