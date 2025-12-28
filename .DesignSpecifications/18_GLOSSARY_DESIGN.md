# 📖 GLOSSARY DESIGN - Quy Chuẩn Thiết Kế Từ Điển Thuật Ngữ

---

## 📋 DOCUMENT INFORMATION (Thông tin tài liệu)

| Thuộc tính | Giá trị |
|------------|---------|
| **Tên** | 18_GLOSSARY_DESIGN |
| **Phiên bản** | 1.0 |
| **Ngày tạo** | 2025-12-28 |
| **Mô tả** | Quy chuẩn viết và duy trì file GLOSSARY.md |

---

## 1. 🎯 PURPOSE (Mục đích)

GLOSSARY.md là file **từ điển thuật ngữ** tập trung, giúp:

- Giải thích thuật ngữ DevOps một cách nhất quán
- Là điểm tham chiếu cho tất cả modules
- Giữ nguyên thuật ngữ tiếng Anh (không dịch)

---

## 2. 📁 LOCATION (Vị trí)

```
DevOps-Journey/
├── resources/
│   ├── GLOSSARY.md          # ⭐ File chính
│   └── SOFTWARE_LINKS.md
└── ...
```

---

## 3. 📋 STRUCTURE (Cấu trúc)

### 3.1 YAML Front-matter

```yaml
---
title: "DevOps Glossary - Từ Điển Thuật Ngữ"
version: "1.0"
last_updated: "YYYY-MM-DD"
total_terms: <số lượng>
---
```

### 3.2 Required Sections (Các phần bắt buộc)

| # | Section | Mô tả |
|---|---------|-------|
| 1 | Navigation Index | Bảng chữ cái A-Z links |
| 2 | Terms by Category | Nhóm theo chủ đề |
| 3 | Term Entries | Định nghĩa từng thuật ngữ |

---

## 4. 📝 TEMPLATE (Mẫu)

```markdown
---
title: "DevOps Glossary - Từ Điển Thuật Ngữ"
version: "1.0"
last_updated: "2025-12-28"
total_terms: 50
---

# 📖 GLOSSARY - Từ Điển Thuật Ngữ DevOps

---

## 🔤 INDEX (Mục lục)

[A](#a) | [B](#b) | [C](#c) | [D](#d) | [E](#e) | [F](#f) | [G](#g) | [H](#h) | [I](#i) | [J](#j) | [K](#k) | [L](#l) | [M](#m) | [N](#n) | [O](#o) | [P](#p) | [Q](#q) | [R](#r) | [S](#s) | [T](#t) | [U](#u) | [V](#v) | [W](#w) | [X](#x) | [Y](#y) | [Z](#z)

---

## 📂 CATEGORIES (Phân loại)

| Category | Terms |
|----------|-------|
| 🐳 Containerization | Docker, Container, Image, Registry |
| ☸️ Orchestration | Kubernetes, Pod, Deployment, Service |
| 🔄 CI/CD | Pipeline, Build, Deploy, Artifact |
| ☁️ Cloud | AWS, EC2, S3, VPC |
| 🔒 Security | TLS, SSH, Secrets, RBAC |

---

## A

### API
**Định nghĩa:** Application Programming Interface - Giao diện lập trình ứng dụng.

**Ngữ cảnh:** Dùng để giao tiếp giữa các services trong microservices architecture.

**Ví dụ:**
```bash
curl -X GET https://api.example.com/users
```

**Xem thêm:** [REST](#rest), [HTTP](#http)

---

### Artifact

**Định nghĩa:** Sản phẩm đầu ra của quá trình build (file JAR, Docker image, binary...).

**Ngữ cảnh:** Artifacts được lưu trữ trong registry để deploy.

**Xem thêm:** [Build](#build), [Registry](#registry)

---

## C

### Container

**Định nghĩa:** Đơn vị đóng gói ứng dụng cùng dependencies, chạy độc lập trên host OS.

**Ngữ cảnh:** Containers nhẹ hơn VMs vì share kernel với host.

**So sánh:**

| Container | Virtual Machine |
|-----------|-----------------|
| Share kernel | Full OS |
| MB size | GB size |
| Seconds to start | Minutes to start |

**Xem thêm:** [Docker](#docker), [Image](#image)

---

[⬆️ Back to Index](#-index-mục-lục)

---

## D

### Docker

**Định nghĩa:** Nền tảng containerization phổ biến nhất, cho phép đóng gói và chạy ứng dụng trong containers.

**Ngữ cảnh:** Docker là công cụ cốt lõi trong DevOps workflow.

**Commands cơ bản:**

```bash
docker build -t myapp .
docker run -d -p 80:80 myapp
docker ps
```

**Xem thêm:** [Container](#container), [Image](#image), [Dockerfile](#dockerfile)

---

[Tiếp tục với các thuật ngữ khác...]

---

## 📚 REFERENCES (Tham khảo)

- [Docker Documentation](https://docs.docker.com/)
- [Kubernetes Glossary](https://kubernetes.io/docs/reference/glossary/)
- [AWS Glossary](https://docs.aws.amazon.com/general/latest/gr/glos-chap.html)

---

[⬅️ Home](../README.md) | [📚 Resources](./README.md)

```

---

## 5. 📏 TERM ENTRY FORMAT (Định dạng mục thuật ngữ)

### 5.1 Required Fields (Bắt buộc)

```markdown
### <Term Name>
**Định nghĩa:** <Giải thích ngắn gọn, 1-2 câu>

**Ngữ cảnh:** <Khi nào/ở đâu thuật ngữ này được dùng>
```

### 5.2 Optional Fields (Tùy chọn)

```markdown
**Ví dụ:**
```bash
<code example>
```

**So sánh:**

| A | B |
|---|---|
| ... | ... |

**Xem thêm:** [Term1](#term1), [Term2](#term2)

```

---

## 6. ✍️ WRITING RULES (Quy tắc viết)

### 6.1 Thuật ngữ

| Quy tắc | Ví dụ |
|---------|-------|
| **GIỮ NGUYÊN tiếng Anh** | Container, Pod, Pipeline |
| Anchor ID = lowercase + hyphen | `### Docker Compose` → `#docker-compose` |
| Sắp xếp A-Z | API → Artifact → Build → ... |

### 6.2 Định nghĩa

| ✅ NÊN | ❌ KHÔNG NÊN |
|--------|--------------|
| Ngắn gọn, 1-2 câu | Quá dài, lan man |
| Dùng "Định nghĩa:" đầu tiên | Không có label |
| Giải thích bằng tiếng Việt | Dịch thuật ngữ |

### 6.3 Cross-references

```markdown
**Xem thêm:** [Docker](#docker), [Kubernetes](#kubernetes)
```

---

## 7. 🔗 LINKING FROM MODULES (Liên kết từ Modules)

### 7.1 Cách link (Theo CONTENT_STANDARDS)

Lần **đầu tiên** thuật ngữ xuất hiện trong mỗi file → Link về GLOSSARY:

```markdown
[Docker](../../resources/GLOSSARY.md#docker) là nền tảng [containerization](../../resources/GLOSSARY.md#container) phổ biến nhất.
```

### 7.2 Relative paths

| Từ | Đường dẫn |
|----|-----------|
| Track README | `../resources/GLOSSARY.md#term` |
| Module file | `../../resources/GLOSSARY.md#term` |
| Nested file | `../../../resources/GLOSSARY.md#term` |

---

## 8. ✅ CHECKLIST (Danh sách kiểm tra)

### Khi thêm thuật ngữ mới

- [ ] Đúng format entry (Định nghĩa, Ngữ cảnh)
- [ ] Sắp xếp đúng theo A-Z
- [ ] Anchor ID đúng (lowercase, hyphen)
- [ ] Thêm cross-references nếu có
- [ ] Cập nhật `total_terms` trong YAML
- [ ] Cập nhật INDEX nếu thêm chữ cái mới

### Review GLOSSARY

- [ ] Không có thuật ngữ trùng lặp
- [ ] Tất cả links hoạt động
- [ ] Categories được cập nhật
- [ ] Back to Index links hoạt động

---

## 9. 📊 CATEGORIES (Các nhóm thuật ngữ)

| Category | Emoji | Ví dụ thuật ngữ |
|----------|-------|-----------------|
| Containerization | 🐳 | Docker, Image, Container, Registry |
| Orchestration | ☸️ | Kubernetes, Pod, Deployment, Service, Helm |
| CI/CD | 🔄 | Pipeline, Build, Deploy, Artifact, Jenkins |
| Cloud | ☁️ | AWS, EC2, S3, VPC, Terraform |
| Security | 🔒 | TLS, SSH, Secrets, RBAC, Vault |
| Networking | 🌐 | DNS, Load Balancer, Ingress, Proxy |
| Monitoring | 📊 | Prometheus, Grafana, Logs, Metrics |
| Version Control | 📝 | Git, Branch, Merge, Commit, PR |

---

## 10. 📚 RELATED FILES (Files liên quan)

| File | Liên quan |
|------|-----------|
| [01_CONTENT_STANDARDS.md](./01_CONTENT_STANDARDS.md) | Quy tắc link về GLOSSARY (section 3.7) |
| [resources/GLOSSARY.md](../resources/GLOSSARY.md) | File GLOSSARY thực tế |
| [resources/SOFTWARE_LINKS.md](../resources/SOFTWARE_LINKS.md) | Links download tools |

---

*Cập nhật: 2025-12-28 | Phiên bản: 1.0*
