# 💪 Exercises: Network Basics

> Bài tập tự luyện về Networking.

---

## Exercise 1: Subnet Calculation ⭐

Cho network `192.168.10.0/26`, tính:

1. Subnet mask
2. Số hosts khả dụng
3. Network address
4. Broadcast address
5. Usable IP range

---

## Exercise 2: DNS Investigation ⭐

1. Tìm tất cả DNS records của `google.com`
2. Tìm mail servers (MX records) của `microsoft.com`
3. Trace DNS resolution path của `github.com`
4. Tìm authoritative name servers

---

## Exercise 3: Network Diagnostics ⭐⭐

Viết script diagnose connectivity issues:

```bash
#!/bin/bash
# diagnose.sh
# Input: hostname or IP
# Output: Diagnostic report
```

Checks:

- Local interface status
- Gateway reachability
- DNS resolution
- Target reachability
- Port connectivity (80, 443)

---

## Exercise 4: Port Scanner ⭐⭐

Viết script scan ports:

```python
#!/usr/bin/env python3
# port_scanner.py

def scan_ports(host, ports):
    """
    Scan specified ports on host.
    Return list of open ports.
    """
    pass
```

---

## Exercise 5: HTTP Client ⭐⭐

Sử dụng cURL hoặc Python requests:

1. GET request với custom headers
2. POST request với JSON body
3. Follow redirects và log each hop
4. Download file với progress
5. Test API với authentication

---

## Exercise 6: Firewall Rules ⭐⭐

Thiết kế firewall rules cho web server:

Requirements:

- Allow SSH từ management network (10.0.0.0/8)
- Allow HTTP/HTTPS từ anywhere
- Allow MySQL từ app servers (192.168.1.0/24)
- Block everything else
- Log dropped packets

---

## Exercise 7: Network Monitoring ⭐⭐⭐

Viết script monitor network:

```python
#!/usr/bin/env python3
# network_monitor.py

class NetworkMonitor:
    def check_hosts(self, hosts: list) -> dict:
        """Ping multiple hosts concurrently."""
        pass
    
    def check_ports(self, host: str, ports: list) -> dict:
        """Check multiple ports."""
        pass
    
    def measure_latency(self, host: str, count: int) -> dict:
        """Measure average latency."""
        pass
```

---

## Exercise 8: SSL Certificate Checker ⭐⭐⭐

Viết tool check SSL certificates:

```python
#!/usr/bin/env python3
# ssl_checker.py

def check_certificate(hostname: str) -> dict:
    """
    Return:
    - Issuer
    - Subject
    - Valid from/to
    - Days until expiration
    - Is expired
    """
    pass
```

---

## 📝 Checklist

- [ ] Exercise 1: Subnet Calculation
- [ ] Exercise 2: DNS Investigation
- [ ] Exercise 3: Network Diagnostics
- [ ] Exercise 4: Port Scanner
- [ ] Exercise 5: HTTP Client
- [ ] Exercise 6: Firewall Rules
- [ ] Exercise 7: Network Monitoring
- [ ] Exercise 8: SSL Checker

---

**[← Back to README](./README.md)** | **[View Solutions →](./SOLUTIONS.md)**
