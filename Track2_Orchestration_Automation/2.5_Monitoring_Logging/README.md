# 📊 Module 2.5: Monitoring & Logging

[![Duration](https://img.shields.io/badge/Duration-1%20week-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Intermediate-orange?style=flat-square)](.)

> **Observability** - Monitor and debug distributed systems.
>
> *Khả năng quan sát - Giám sát và debug hệ thống phân tán.*

---

## 🎯 Learning Objectives (Mục tiêu học tập)

After this module, you will (Sau module này, bạn sẽ):

- ✅ Understand observability pillars - metrics, logs, traces (Hiểu các trụ cột observability)
- ✅ Setup Prometheus & Grafana (Thiết lập Prometheus & Grafana)
- ✅ Create dashboards and alerts (Tạo dashboard và cảnh báo)
- ✅ Implement centralized logging with ELK/Loki (Triển khai logging tập trung)
- ✅ Collect application metrics (Thu thập metrics ứng dụng)
- ✅ Configure alerting and oncall (Cấu hình cảnh báo và trực)

---

## 📚 Content (Nội dung)

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

### 3. PromQL Basics (PromQL cơ bản)

```promql
# CPU usage (Sử dụng CPU)
rate(process_cpu_seconds_total[5m])

# Memory usage (Sử dụng bộ nhớ)
process_resident_memory_bytes / 1024 / 1024

# HTTP request rate (Tỷ lệ yêu cầu HTTP)
rate(http_requests_total[5m])

# Error rate (Tỷ lệ lỗi)
rate(http_requests_total{status="500"}[5m])

# 95th percentile latency (Độ trễ phân vị 95)
histogram_quantile(0.95, rate(http_request_duration_seconds_bucket[5m]))
```

### 4. Alerting (Cảnh báo)

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

## 📝 Module Files (Các file trong Module)

| File | Description |
|------|---------------------|
| [LABS.md](./LABS.md) | Hands-on labs (Bài thực hành) |
| [QUIZ.md](./QUIZ.md) | Knowledge check (Kiểm tra kiến thức) |
| [EXERCISES.md](./EXERCISES.md) | Exercises (Bài tập) |
| [PROJECT.md](./PROJECT.md) | Mini project (Dự án nhỏ) |
| [SOLUTIONS.md](./SOLUTIONS.md) | Solutions (Đáp án) |
| [CHEATSHEET.md](./CHEATSHEET.md) | Quick reference (Tra cứu nhanh) |

---

<div align="center">

### 🔗 Module Navigation (Điều hướng Module)

| ← Previous | Current | Next → |
|:------------------:|:------------------:|:-------------:|
| [2.4 Kubernetes](../2.4_Kubernetes_Core/) | **2.5 Monitoring** | [2.6 Capstone](../2.6_Capstone_Project/) |

---

**Master observability for production systems! 📊**

*Thành thạo khả năng quan sát cho hệ thống production!*

</div>
