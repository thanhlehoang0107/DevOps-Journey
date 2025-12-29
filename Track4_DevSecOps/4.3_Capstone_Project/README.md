# 🏆 Module 4.3: DevSecOps Capstone Project

> **Secure CI/CD Pipeline**
>
> *Pipeline CI/CD an toàn*

---

## 🎯 Project Overview (Tổng quan dự án)

Build secure CI/CD pipeline with all security controls.

*Xây dựng pipeline CI/CD an toàn với tất cả security controls.*

---

## 📋 Requirements (Yêu cầu)

### Pipeline Stages (Các giai đoạn Pipeline)

1. **Source** - Secret scanning (Gitleaks) - *Quét secrets*
2. **Build** - SAST (SonarQube), Dependency scan - *Quét mã nguồn, dependencies*
3. **Test** - Security tests - *Kiểm thử bảo mật*
4. **Container** - Image scanning (Trivy) - *Quét image*
5. **Deploy** - Policy checks (OPA) - *Kiểm tra chính sách*
6. **Runtime** - Monitoring - *Giám sát*

### Security Controls (Kiểm soát bảo mật)

- [ ] No secrets in code (Không có secrets trong code)
- [ ] Dependency vulnerabilities addressed (Đã xử lý lỗ hổng dependencies)
- [ ] Container runs as non-root (Container chạy không phải root)
- [ ] Network policies (Chính sách mạng)
- [ ] Audit logging (Ghi nhật ký kiểm toán)
- [ ] Alerting (Cảnh báo)

### Tools (Công cụ)

- GitHub Actions / Jenkins
- SonarQube
- Trivy
- HashiCorp Vault
- OPA

---

## ✅ Deliverables (Sản phẩm bàn giao)

- [ ] Complete CI/CD pipeline (Pipeline CI/CD hoàn chỉnh)
- [ ] All security scans passing (Tất cả quét bảo mật pass)
- [ ] Security documentation (Tài liệu bảo mật)
- [ ] Incident response plan (Kế hoạch xử lý sự cố)

---

## 📊 Evaluation (Đánh giá)

| Criteria (Tiêu chí) | Weight (Trọng số) |
|---------------------|-------------------|
| Pipeline implementation (Triển khai pipeline) | 30% |
| Security controls (Kiểm soát bảo mật) | 30% |
| Automation (Tự động hóa) | 20% |
| Documentation (Tài liệu) | 20% |

---

<div align="center">

### 🔗 Module Navigation (Điều hướng Module)

| ← Previous | Current | Next → |
|:------------------:|:------------------:|:-------------:|
| [4.2 Infra Security](../4.2_Infra_Security/) | **4.3 Capstone** | [Track 5](../../Track5_Career_Path/) |

---

**Good luck! 🚀**

*Chúc may mắn!*

</div>
