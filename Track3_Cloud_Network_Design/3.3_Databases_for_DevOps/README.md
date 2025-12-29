# 🗄️ Module 3.3: Databases for DevOps

[![Duration](https://img.shields.io/badge/Duration-1%20week-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Intermediate-orange?style=flat-square)](.)

> **Database Management** - RDS, NoSQL, Caching, and Migrations.
>
> *Quản lý Database - RDS, NoSQL, Caching, và Migrations.*

---

## 🎯 Learning Objectives (Mục tiêu học tập)

After this module, you will (Sau module này, bạn sẽ):

- ✅ Manage RDS (MySQL, PostgreSQL) (Quản lý RDS)
- ✅ Work with NoSQL databases - DynamoDB, MongoDB (Làm việc với NoSQL)
- ✅ Implement caching with Redis/ElastiCache (Triển khai caching)
- ✅ Perform database migrations (Thực hiện migrations)
- ✅ Configure backup and recovery (Cấu hình backup và recovery)
- ✅ Tune performance (Tối ưu hiệu suất)

---

## 📚 Content (Nội dung)

### 1. RDS

```bash
# Create RDS instance (Tạo RDS instance)
aws rds create-db-instance \
  --db-instance-identifier mydb \
  --db-instance-class db.t3.micro \
  --engine postgres \
  --master-username admin \
  --master-user-password secret123 \
  --allocated-storage 20
```

### 2. Redis

```bash
# Connect (Kết nối)
redis-cli -h myredis.xxx.cache.amazonaws.com

# Basic commands (Lệnh cơ bản)
SET key "value"
GET key
EXPIRE key 3600
```

### 3. Migrations

```bash
# Using Flyway (Sử dụng Flyway)
flyway -url=jdbc:postgresql://host:5432/db migrate

# Using Django (Sử dụng Django)
python manage.py migrate
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
| [3.2 AWS Core](../3.2_AWS_Core_Services/) | **3.3 Databases** | [3.4 Ansible](../3.4_Config_Management_Ansible/) |

---

**Master database management! 🗄️**

*Thành thạo quản lý database!*

</div>
