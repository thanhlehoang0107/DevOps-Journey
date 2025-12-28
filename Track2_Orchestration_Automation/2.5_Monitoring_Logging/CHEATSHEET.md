# Monitoring Cheatsheet

## Prometheus

```yaml
scrape_configs:
  - job_name: 'app'
    static_configs:
      - targets: ['localhost:8080']
```

## PromQL

```
rate(http_requests_total[5m])
```
