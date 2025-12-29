# 📊 Module 2.5: Monitoring & Logging

[![Duration](https://img.shields.io/badge/Duration-1%20week-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Intermediate-orange?style=flat-square)](.)

> **Observability** - Monitor và debug distributed systems.

---

## 🎯 Learning Objectives

- ✅ Hiểu observability pillars (metrics, logs, traces)
- ✅ Setup Prometheus & Grafana
- ✅ Create dashboards và alerts
- ✅ Centralized logging với ELK/Loki
- ✅ Application metrics
- ✅ Alerting và oncall

---

## 📚 Content

### 1. Prometheus

```yaml
# prometheus.yml
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['localhost:9090']
  
  - job_name: 'node'
    static_configs:
      - targets: ['node-exporter:9100']
  
  - job_name: 'app'
    static_configs:
      - targets: ['app:3000']
```

### 2. Grafana Dashboard

```json
{
  "panels": [
    {
      "title": "CPU Usage",
      "type": "graph",
      "targets": [
        {
          "expr": "rate(process_cpu_seconds_total[5m])"
        }
      ]
    }
  ]
}
```

### 3. PromQL Basics

```promql
# CPU usage
rate(process_cpu_seconds_total[5m])

# Memory usage
process_resident_memory_bytes / 1024 / 1024

# HTTP request rate
rate(http_requests_total[5m])

# Error rate
rate(http_requests_total{status="500"}[5m])

# 95th percentile latency
histogram_quantile(0.95, rate(http_request_duration_seconds_bucket[5m]))
```

### 4. Alerting

```yaml
# alerting.rules.yml
groups:
  - name: example
    rules:
      - alert: HighCPU
        expr: rate(process_cpu_seconds_total[5m]) > 0.8
        for: 5m
        labels:
          severity: warning
        annotations:
          summary: "High CPU usage"
```

### 5. Loki Logging

```yaml
# loki-config.yaml
auth_enabled: false

server:
  http_listen_port: 3100

ingester:
  lifecycler:
    ring:
      replication_factor: 1

schema_config:
  configs:
    - from: 2020-01-01
      store: boltdb
      object_store: filesystem
      schema: v11
      index:
        prefix: index_
        period: 168h
```

---

## 📝 Module Files

| File | Description |
|------|-------------|
| [LABS.md](./LABS.md) | Hands-on labs |
| [QUIZ.md](./QUIZ.md) | Knowledge check |
| [EXERCISES.md](./EXERCISES.md) | Exercises |
| [PROJECT.md](./PROJECT.md) | Mini project |
| [SOLUTIONS.md](./SOLUTIONS.md) | Solutions |
| [CHEATSHEET.md](./CHEATSHEET.md) | Quick reference |
