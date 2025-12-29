# 🏆 CAPSTONE DESIGN - Quy Chuẩn Thiết Kế Capstone Project

---

## 📋 DOCUMENT INFORMATION (Thông tin tài liệu)

| Thuộc tính | Giá trị |
|------------|---------|
| **Tên** | Capstone Design Specification |
| **Phiên bản** | 1.0 |
| **Ngày tạo** | 2025-12-28 |
| **Mô tả** | Thiết kế riêng cho Capstone Projects cuối mỗi Track |

---

## 1. 🎯 CAPSTONE VS MODULE PROJECT (Dự án tốt nghiệp của mỗi module)

| Tiêu chí | Module PROJECT.md | Capstone Project |
|----------|-------------------|------------------|
| **Phạm vi** | 1 module | Toàn bộ Track |
| **Thời gian** | 2-4 giờ | 8-20 giờ |
| **Độ phức tạp** | Áp dụng 1-2 concepts | Tích hợp tất cả modules |
| **Portfolio** | Có thể | **Bắt buộc** |
| **Files** | 7 files chuẩn | Chỉ README + SOLUTIONS |

---

## 2. 📁 CAPSTONE STRUCTURE (Cấu trúc Capstone)

```
X.Y_Capstone_Project/
├── images/                    # Screenshots, diagrams
├── starter-code/              # Code khởi đầu (nếu có)
│   └── ...
├── README.md                  # Đề bài chi tiết
└── SOLUTIONS.md               # Giải pháp tham khảo
```

> 📝 **Lưu ý:** Capstone **KHÔNG có** CHEATSHEET, LABS, QUIZ, EXERCISES vì nó là dự án tổng hợp.

---

## 3. 📋 REQUIRED SECTIONS (Các phần bắt buộc) - README.md

| # | Section | Mô tả | Bắt buộc |
|---|---------|-------|----------|
| 1 | **YAML Front-matter** | Metadata + technologies | ✅ |
| 2 | **Project Title** | Tên dự án hấp dẫn | ✅ |
| 3 | **Project Overview** | Mô tả, business context | ✅ |
| 4 | **Learning Objectives** | Tổng hợp skills từ Track | ✅ |
| 5 | **Prerequisites** | Tất cả modules trong Track | ✅ |
| 6 | **Architecture Diagram** ⭐ | Sơ đồ hệ thống hoàn chỉnh | ✅ |
| 7 | **Technical Stack** | Bảng công nghệ sử dụng | ✅ |
| 8 | **Requirements** | Functional, Non-functional, Bonus | ✅ |
| 9 | **Milestones** | Chia thành 3-5 phases | ✅ |
| 10 | **Deliverables** | Files/artifacts cần nộp | ✅ |
| 11 | **Evaluation Criteria** | Rubric chấm điểm chi tiết | ✅ |
| 12 | **Submission** | Hướng dẫn nộp bài | ✅ |
| 13 | **Tips & Resources** | Gợi ý và tài liệu | ⭕ |
| 14 | **Navigation Footer** | Điều hướng | ✅ |

---

## 4. 📝 TEMPLATE (Mẫu) - README.md

```markdown
---
module: "X.Y"
title: "Capstone Project – <Tên Dự Án>"
track: "X"
version: "1.0"
last_updated: "YYYY-MM-DD"
difficulty: "Advanced"
estimated_time: "15-20 hours"
technologies: ["Tech1", "Tech2", "Tech3", "Tech4"]
---

# 🏆 CAPSTONE PROJECT: <Tên Dự Án>

---

## 1. Project Overview (Tổng quan dự án)

### Bối cảnh

Bạn được thuê làm DevOps Engineer cho công ty XYZ. Công ty đang cần [mô tả business problem]...

### Mục tiêu

Xây dựng một hệ thống hoàn chỉnh bao gồm:
- Component 1
- Component 2
- Component 3

### Tại sao dự án này quan trọng?

- Tích hợp **tất cả kiến thức** từ Track X
- Có **sản phẩm hoàn chỉnh** để demo
- Chuẩn bị cho **portfolio** và **phỏng vấn**

---

## 2. Learning Objectives (Mục tiêu học)

Sau khi hoàn thành, bạn sẽ chứng minh được khả năng:

| Module | Skill |
|--------|-------|
| X.1 | Skill từ module X.1 |
| X.2 | Skill từ module X.2 |
| X.3 | Skill từ module X.3 |
| ... | ... |

---

## 3. Prerequisites (Yêu cầu tiên quyết)

### Kiến thức (Bắt buộc)

- [ ] ✅ Hoàn thành Module X.1 – <Tên>
- [ ] ✅ Hoàn thành Module X.2 – <Tên>
- [ ] ✅ Hoàn thành Module X.3 – <Tên>
- [ ] ✅ ...

### Công cụ

```bash
# Verify tất cả tools
./Setup_Environment/scripts/linux/verify_trackX.sh
```

---

## 4. Architecture Diagram (Sơ đồ kiến trúc)

```
┌─────────────────────────────────────────────────────────────────────────┐
│                        CAPSTONE ARCHITECTURE                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ┌──────────────┐    ┌──────────────┐    ┌──────────────┐              │
│  │   Frontend   │    │   Backend    │    │   Database   │              │
│  │   (NGINX)    │───▶│   (Node.js)  │───▶│  (PostgreSQL)│              │
│  └──────────────┘    └──────────────┘    └──────────────┘              │
│         │                   │                   │                        │
│         └───────────────────┼───────────────────┘                        │
│                             │                                            │
│                    ┌────────▼────────┐                                   │
│                    │   Docker Compose │                                  │
│                    └────────┬────────┘                                   │
│                             │                                            │
│                    ┌────────▼────────┐                                   │
│                    │   CI/CD Pipeline │                                  │
│                    │   (GitHub Actions)│                                 │
│                    └─────────────────┘                                   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Component Description

| Component | Technology | Mô tả |
|-----------|------------|-------|
| Frontend | NGINX | Serve static files |
| Backend | Node.js | REST API |
| Database | PostgreSQL | Data storage |
| Container | Docker Compose | Orchestration |
| CI/CD | GitHub Actions | Automation |

---

## 5. Technical Stack (Công nghệ sử dụng)

| Layer | Technology | Version |
|-------|------------|---------|
| Container | Docker | 24.x |
| Orchestration | Docker Compose | 2.x |
| Web Server | NGINX | 1.25 |
| ... | ... | ... |

---

## 6. Requirements (Yêu cầu)

### 6.1 Functional Requirements (70 điểm)

| ID | Requirement | Điểm |
|----|-------------|------|
| FR1 | Requirement 1 | 15 |
| FR2 | Requirement 2 | 15 |
| FR3 | Requirement 3 | 15 |
| FR4 | Requirement 4 | 15 |
| FR5 | Requirement 5 | 10 |

### 6.2 Non-functional Requirements (20 điểm)

| ID | Requirement | Điểm |
|----|-------------|------|
| NFR1 | Documentation đầy đủ | 10 |
| NFR2 | Code quality | 5 |
| NFR3 | Security best practices | 5 |

### 6.3 Bonus Features (+20 điểm)

| ID | Feature | Điểm bonus |
|----|---------|------------|
| B1 | Bonus feature 1 | +10 |
| B2 | Bonus feature 2 | +10 |

---

## 7. Milestones (Các mốc)

### Milestone 1: Setup & Foundation (3-4 hours)

- [ ] Setup project structure
- [ ] Configure Docker Compose
- [ ] Basic services running

**Checkpoint:** `docker compose up` thành công

---

### Milestone 2: Core Implementation (6-8 hours)

- [ ] Implement FR1, FR2
- [ ] Implement FR3, FR4
- [ ] Integration testing

**Checkpoint:** All services communicate correctly

---

### Milestone 3: CI/CD & Documentation (4-5 hours)

- [ ] Setup GitHub Actions
- [ ] Write documentation
- [ ] Final testing

**Checkpoint:** Push triggers pipeline

---

## 8. Deliverables (Sản phẩm giao)

```
capstone-project/
├── docker-compose.yml        ✅ Required
├── .github/
│   └── workflows/
│       └── ci.yml            ✅ Required
├── frontend/
│   └── ...                   ✅ Required
├── backend/
│   └── ...                   ✅ Required
├── docs/
│   └── ARCHITECTURE.md       ✅ Required
├── README.md                 ✅ Required
└── screenshots/
    ├── running-app.png       ✅ Required
    └── ci-pipeline.png       ✅ Required
```

---

## 9. Evaluation Rubric (Thang điểm)

| Criteria | Weight | Description |
|----------|--------|-------------|
| **Functionality** | 40% | Tất cả FR hoạt động đúng |
| **Architecture** | 20% | Thiết kế hợp lý, scalable |
| **Code Quality** | 15% | Clean, readable, commented |
| **Documentation** | 15% | README, diagrams đầy đủ |
| **CI/CD** | 10% | Pipeline hoạt động |
| **Bonus** | +20% | Extra features |

### Grading Scale

| Score | Grade | Đánh giá |
|-------|-------|----------|
| 90-100+ | A | Xuất sắc - Portfolio ready ⭐⭐⭐ |
| 80-89 | B | Tốt - Minor improvements needed ⭐⭐ |
| 70-79 | C | Pass - Meets basic requirements ⭐ |
| < 70 | F | Cần làm lại |

---

## 10. Submission Guidelines (Hướng dẫn nộp)

1. **GitHub Repository:**
   - Public repo với tên: `devops-capstone-trackX`
   - Include `.gitignore` (no secrets, no node_modules)

2. **README phải có:**
   - How to run locally
   - Architecture diagram
   - Screenshots

3. **Deadline:** [Specify deadline]

---

## 11. Tips & Resources (Mẹo và tài nguyên)

### Tips

1. **Bắt đầu từ Milestone 1** - Đừng skip
2. **Test từng phần** trước khi integrate
3. **Commit thường xuyên** với message rõ ràng

### Resources

- [Starter Code](./starter-code/) (nếu có)
- [Reference Architecture](link)
- [Track X Documentation](../README.md)

---

[⬅️ Module trước](../X.Y-1_ModuleName/README.md) | [📚 Track X](../README.md) | [Track X+1 ➡️](../../TrackX+1_Name/README.md)

```

---

## 5. ✅ REVIEW CHECKLIST (Danh sách kiểm tra)

- [ ] Business context rõ ràng
- [ ] Tích hợp tất cả modules trong Track
- [ ] Architecture diagram hoàn chỉnh
- [ ] Requirements có điểm số cụ thể
- [ ] Milestones với checkpoints
- [ ] Evaluation rubric chi tiết
- [ ] Submission guidelines rõ ràng
- [ ] **Navigation Footer** ⭐

---

## 6. 📊 CAPSTONE BY TRACK (Capstone theo Track)

| Track | Capstone Name | Focus |
|-------|---------------|-------|
| 1 | Static Website CI/CD | Docker + NGINX + GitHub Actions |
| 2 | Microservices on K8s | Docker Compose + Kubernetes + Monitoring |
| 3 | Cloud Infrastructure | Terraform + AWS + System Design |
| 4 | Secure CI/CD Pipeline | Security scanning + Hardening |
| 5 | Portfolio & CV | Documentation + Interview prep |

---

*Cập nhật: 2025-12-28 | Phiên bản: 1.0*










