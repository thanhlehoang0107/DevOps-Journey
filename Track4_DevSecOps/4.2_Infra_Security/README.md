# 🛡️ Module 4.2: Infrastructure Security

[![Duration](https://img.shields.io/badge/Duration-1%20week-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Intermediate-orange?style=flat-square)](.)

> **Secure Infrastructure** - Hardening, compliance, and security monitoring.
>
> *Hạ tầng bảo mật - Hardening, tuân thủ, và giám sát bảo mật.*

---

## 🎯 Learning Objectives (Mục tiêu học tập)

After this module, you will (Sau module này, bạn sẽ):

- ✅ Apply cloud security best practices (Áp dụng bảo mật cloud)
- ✅ Implement network security (Triển khai bảo mật mạng)
- ✅ Manage secrets (Quản lý secrets)
- ✅ Understand compliance frameworks (Hiểu các framework tuân thủ)
- ✅ Setup security monitoring (Thiết lập giám sát bảo mật)
- ✅ Perform incident response (Xử lý sự cố)

---

## 📚 Content (Nội dung)

### 1. Secrets Management (Quản lý Secrets)

```bash
# HashiCorp Vault
vault kv put secret/myapp db_password=secret123
vault kv get secret/myapp

# AWS Secrets Manager
aws secretsmanager create-secret \
  --name MySecret \
  --secret-string '{"password":"secret123"}'
```

### 2. AWS Security (Bảo mật AWS)

```bash
# Enable GuardDuty (Bật GuardDuty)
aws guardduty create-detector --enable

# Security Hub
aws securityhub enable-security-hub

# Config Rules (Quy tắc cấu hình)
aws configservice put-config-rule --config-rule file://rule.json
```

### 3. CIS Benchmarks

- OS hardening (Hardening hệ điều hành)
- SSH configuration (Cấu hình SSH)
- Firewall rules (Quy tắc tường lửa)
- Audit logging (Ghi nhật ký kiểm toán)

### 4. Compliance (Tuân thủ)

```yaml
# InSpec
control 'ssh-config' do
  impact 1.0
  title 'SSH configuration'
  
  describe sshd_config do
    its('PermitRootLogin') { should eq 'no' }
    its('PasswordAuthentication') { should eq 'no' }
  end
end
```

---

## 📝 Module Files (Các file trong Module)

| File | Description (Mô tả) |
|------|---------------------|
| [LABS.md](./LABS.md) | Hands-on labs (Bài thực hành) |
| [QUIZ.md](./QUIZ.md) | Knowledge check (Kiểm tra kiến thức) |
| [EXERCISES.md](./EXERCISES.md) | Exercises (Bài tập) |
| [SOLUTIONS.md](./SOLUTIONS.md) | Solutions (Đáp án) |

---

<div align="center">

### 🔗 Module Navigation (Điều hướng Module)

| ← Previous (Trước) | Current (Hiện tại) | Next (Tiếp) → |
|:------------------:|:------------------:|:-------------:|
| [4.1 Security Pipeline](../4.1_Security_in_Pipeline/) | **4.2 Infra Security** | [4.3 Capstone](../4.3_Capstone_Project/) |

---

**Secure your infrastructure! 🛡️**

*Bảo mật hạ tầng của bạn!*

</div>
