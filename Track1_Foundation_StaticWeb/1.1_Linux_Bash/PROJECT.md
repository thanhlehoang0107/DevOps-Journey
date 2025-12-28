# Mini Project - Linux & Bash

## System Health Check Script

### Mục tiêu

Viết một bash script `health_check.sh` để kiểm tra và báo cáo tình trạng hệ thống.

### Yêu cầu

Script phải hiển thị:

1. Thông tin hệ thống (hostname, OS)
2. Disk usage
3. Memory usage
4. Top 5 processes sử dụng CPU nhiều nhất
5. Network status

### Đầu ra mong đợi

```
=== System Health Report ===
Date: 2025-12-28 10:00:00
Hostname: devops-server
OS: Ubuntu 22.04

=== Disk Usage ===
/dev/sda1  50G  20G  30G  40%

=== Memory Usage ===
Total: 16GB | Used: 8GB | Free: 8GB

...
```

### Tiêu chí đánh giá

- Script chạy không lỗi
- Hiển thị đầy đủ thông tin
- Code có comments
- Sử dụng functions
