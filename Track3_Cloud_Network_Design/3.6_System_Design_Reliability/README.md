# 🏛️ Module 3.6: System Design & Reliability

> **Building Reliable Systems** - High Availability, Scalability, Disaster Recovery.

---

## 🎯 Learning Objectives

- ✅ High Availability patterns
- ✅ Scalability strategies
- ✅ Disaster Recovery
- ✅ Capacity planning
- ✅ SLAs, SLOs, SLIs
- ✅ Chaos Engineering basics

---

## 📚 Content

### 1. HA Patterns

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

### 2. Scaling

- **Vertical**: Bigger instance
- **Horizontal**: More instances
- **Auto Scaling**: Based on metrics

### 3. DR Strategies

| Strategy | RTO | RPO | Cost |
|----------|-----|-----|------|
| Backup/Restore | Hours | Hours | $ |
| Pilot Light | Minutes | Minutes | $$ |
| Warm Standby | Minutes | Seconds | $$$ |
| Active-Active | Zero | Zero | $$$$ |

### 4. SRE Metrics

- **SLA**: Service Level Agreement (99.9%)
- **SLO**: Service Level Objective (target)
- **SLI**: Service Level Indicator (actual)

---

## 📝 Module Files

- [LABS.md](./LABS.md) | [QUIZ.md](./QUIZ.md) | [EXERCISES.md](./EXERCISES.md)
