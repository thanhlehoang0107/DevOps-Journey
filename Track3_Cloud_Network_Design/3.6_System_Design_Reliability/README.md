# 🏛️ Module 3.6: System Design & Reliability

[![Duration](https://img.shields.io/badge/Duration-1%20week-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Intermediate-orange?style=flat-square)](.)

> **Building Reliable Systems** - High Availability, Scalability, Disaster Recovery.
>
> *Xây dựng hệ thống đáng tin cậy - Tính sẵn sàng cao, Khả năng mở rộng, Khắc phục thảm họa.*

---

## 🎯 Learning Objectives (Mục tiêu học tập)

After this module, you will (Sau module này, bạn sẽ):

- ✅ Implement High Availability patterns (Triển khai mẫu HA)
- ✅ Design Scalability strategies (Thiết kế chiến lược mở rộng)
- ✅ Plan Disaster Recovery (Lập kế hoạch DR)
- ✅ Perform Capacity planning (Quy hoạch dung lượng)
- ✅ Understand SLAs, SLOs, SLIs (Hiểu SLAs, SLOs, SLIs)
- ✅ Learn Chaos Engineering basics (Tìm hiểu Chaos Engineering)

---

## 📚 Content (Nội dung)

### 1. HA Patterns (Mẫu High Availability)

```
┌─────────────────────────────────────────┐
│           Load Balancer                  │
└────────────────┬────────────────────────┘
                 │
    ┌────────────┼────────────┐
    │            │            │
┌───▼───┐    ┌───▼───┐    ┌───▼───┐
│ App 1 │    │ App 2 │    │ App 3 │
│ (AZ-a)│    │ (AZ-b)│    │ (AZ-c)│
└───────┘    └───────┘    └───────┘
```

### 2. Scaling (Mở rộng)

- **Vertical (Theo chiều dọc)**: Bigger instance (Instance lớn hơn)
- **Horizontal (Theo chiều ngang)**: More instances (Nhiều instances hơn)
- **Auto Scaling (Tự động mở rộng)**: Based on metrics (Dựa trên metrics)

### 3. DR Strategies (Chiến lược DR)

| Strategy (Chiến lược) | RTO | RPO | Cost (Chi phí) |
|-----------------------|-----|-----|----------------|
| Backup/Restore (Sao lưu) | Hours (Giờ) | Hours (Giờ) | $ |
| Pilot Light | Minutes (Phút) | Minutes (Phút) | $$ |
| Warm Standby | Minutes (Phút) | Seconds (Giây) | $$$ |
| Active-Active | Zero (Không) | Zero (Không) | $$$$ |

### 4. SRE Metrics

- **SLA**: Service Level Agreement - Thỏa thuận cấp độ dịch vụ (99.9%)
- **SLO**: Service Level Objective - Mục tiêu (target)
- **SLI**: Service Level Indicator - Chỉ số thực tế (actual)

---

## 📝 Module Files (Các file trong Module)

| File | Description |
|------|---------------------|
| [LABS.md](./LABS.md) | Hands-on labs (Bài thực hành) |
| [QUIZ.md](./QUIZ.md) | Knowledge check (Kiểm tra kiến thức) |
| [EXERCISES.md](./EXERCISES.md) | Exercises (Bài tập) |
| [SOLUTIONS.md](./SOLUTIONS.md) | Solutions (Đáp án) |

---

<div align="center">

### 🔗 Module Navigation (Điều hướng Module)

| ← Previous | Current | Next → |
|:------------------:|:------------------:|:-------------:|
| [3.5 Terraform](../3.5_Terraform_IaC/) | **3.6 System Design** | [3.7 Capstone](../3.7_Capstone_Project/) |

---

**Build reliable systems! 🏛️**

*Xây dựng hệ thống đáng tin cậy!*

</div>
