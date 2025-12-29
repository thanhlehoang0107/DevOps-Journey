# 🗄️ Module 3.3: Databases for DevOps

> **Database Management** - RDS, NoSQL, Caching, Migrations.

---

## 🎯 Learning Objectives

- ✅ RDS management (MySQL, PostgreSQL)
- ✅ NoSQL databases (DynamoDB, MongoDB)
- ✅ Caching với Redis/ElastiCache
- ✅ Database migrations
- ✅ Backup và recovery
- ✅ Performance tuning

---

## 📚 Content

### 1. RDS

```bash
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
# Connect
redis-cli -h myredis.xxx.cache.amazonaws.com

# Basic commands
SET key "value"
GET key
EXPIRE key 3600
```

### 3. Migrations

```bash
# Using Flyway
flyway -url=jdbc:postgresql://host:5432/db migrate

# Using Django
python manage.py migrate
```

---

## 📝 Module Files

- [LABS.md](./LABS.md) | [QUIZ.md](./QUIZ.md) | [EXERCISES.md](./EXERCISES.md)
