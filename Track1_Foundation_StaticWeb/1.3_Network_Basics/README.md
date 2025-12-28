# 🌐 Module 1.3: Network Basics

> Hiểu về mạng - Nền tảng cho mọi hệ thống phân tán

---

## 📋 Thông tin Module

| Thuộc tính | Giá trị |
|------------|---------|
| **Thời lượng** | 8-10 giờ |
| **Độ khó** | ⭐ Beginner |
| **Yêu cầu trước** | Module 1.2 hoàn thành |

---

## 🎯 Mục tiêu học tập

- [ ] Hiểu mô hình OSI và TCP/IP
- [ ] Hiểu IP addressing và subnetting
- [ ] Hiểu DNS và cách hoạt động
- [ ] Sử dụng các công cụ network troubleshooting
- [ ] Hiểu HTTP/HTTPS protocol

---

## 📖 Nội dung

### 1. Mô hình OSI và TCP/IP

```
┌─────────────────────────────────────────────────────────────┐
│       OSI Model           │       TCP/IP Model              │
├───────────────────────────┼─────────────────────────────────┤
│ 7. Application            │                                 │
│ 6. Presentation           │    4. Application                │
│ 5. Session                │       (HTTP, DNS, SSH)          │
├───────────────────────────┼─────────────────────────────────┤
│ 4. Transport              │    3. Transport (TCP, UDP)      │
├───────────────────────────┼─────────────────────────────────┤
│ 3. Network                │    2. Internet (IP)             │
├───────────────────────────┼─────────────────────────────────┤
│ 2. Data Link              │                                 │
│ 1. Physical               │    1. Network Access            │
└───────────────────────────┴─────────────────────────────────┘
```

---

### 2. IP Addressing

#### IPv4 Format

```
192.168.1.100
└─┬─┘ └┬┘ └┬┘ └┬┘
  │    │   │   └── Host (0-255)
  │    │   └────── Subnet
  │    └────────── Class B
  └─────────────── Class B
```

#### Các dải IP quan trọng

| Loại | Dải | Mô tả |
|------|-----|-------|
| **Private** | 192.168.0.0/16 | Mạng nội bộ (phổ biến) |
| **Private** | 10.0.0.0/8 | Mạng nội bộ (lớn) |
| **Private** | 172.16.0.0/12 | Mạng nội bộ |
| **Loopback** | 127.0.0.1 | Localhost |
| **Public** | Còn lại | Internet |

#### CIDR Notation

| CIDR | Subnet Mask | Hosts |
|------|-------------|-------|
| /24 | 255.255.255.0 | 254 |
| /16 | 255.255.0.0 | 65,534 |
| /8 | 255.0.0.0 | 16,777,214 |

---

### 3. Ports và Protocols

#### Common Ports

| Port | Protocol | Service |
|------|----------|---------|
| 22 | TCP | SSH |
| 80 | TCP | HTTP |
| 443 | TCP | HTTPS |
| 3306 | TCP | MySQL |
| 5432 | TCP | PostgreSQL |
| 6379 | TCP | Redis |
| 27017 | TCP | MongoDB |

#### TCP vs UDP

| TCP | UDP |
|-----|-----|
| Connection-oriented | Connectionless |
| Reliable (retransmit) | Fast (no guarantee) |
| HTTP, SSH, SMTP | DNS, VoIP, Streaming |

---

### 4. DNS (Domain Name System)

```
Browser request: www.example.com
          │
          ▼
   ┌──────────────┐
   │ Local Cache  │──► Found? Return IP
   └──────────────┘
          │
          ▼
   ┌──────────────┐
   │ DNS Resolver │ (ISP hoặc 8.8.8.8)
   └──────────────┘
          │
          ▼
   ┌──────────────┐
   │ Root Server  │ (.)
   └──────────────┘
          │
          ▼
   ┌──────────────┐
   │  TLD Server  │ (.com)
   └──────────────┘
          │
          ▼
   ┌───────────────┐
   │ Authoritative │ (example.com)
   │    Server     │
   └───────────────┘
          │
          ▼
     93.184.216.34
```

#### DNS Record Types

| Record | Mô tả | Ví dụ |
|--------|-------|-------|
| **A** | Domain → IPv4 | example.com → 93.184.216.34 |
| **AAAA** | Domain → IPv6 | example.com → 2001:db8::1 |
| **CNAME** | Alias | <www.example.com> → example.com |
| **MX** | Mail server | example.com → mail.example.com |
| **TXT** | Text info | SPF, DKIM records |

---

### 5. HTTP/HTTPS

#### HTTP Methods

| Method | Mô tả | Ví dụ |
|--------|-------|-------|
| GET | Lấy dữ liệu | Xem trang web |
| POST | Tạo mới | Submit form |
| PUT | Update (toàn bộ) | Update user info |
| PATCH | Update (một phần) | Đổi password |
| DELETE | Xóa | Xóa tài khoản |

#### HTTP Status Codes

| Code | Ý nghĩa |
|------|---------|
| **2xx** | Success |
| 200 | OK |
| 201 | Created |
| **3xx** | Redirect |
| 301 | Moved Permanently |
| 302 | Found (Temporary) |
| **4xx** | Client Error |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| **5xx** | Server Error |
| 500 | Internal Server Error |
| 502 | Bad Gateway |
| 503 | Service Unavailable |

---

### 6. Network Troubleshooting Tools

#### ping - Kiểm tra connectivity

```bash
ping google.com
ping -c 4 google.com    # Chỉ ping 4 lần

# Output:
# PING google.com (142.250.X.X): 56 data bytes
# 64 bytes from 142.250.X.X: icmp_seq=0 ttl=117 time=10.5 ms
```

#### traceroute - Xem đường đi của packet

```bash
traceroute google.com
tracert google.com      # Windows
```

#### nslookup - Tra cứu DNS

```bash
nslookup google.com
nslookup -type=MX google.com
```

#### dig - DNS lookup nâng cao

```bash
dig google.com
dig google.com A
dig google.com MX
dig +short google.com
```

#### netstat - Xem connections

```bash
netstat -tulpn          # Linux: listening ports
netstat -an             # All connections
ss -tulpn               # Modern netstat
```

#### curl - HTTP requests

```bash
# GET request
curl https://api.github.com

# Xem headers
curl -I https://google.com

# POST request
curl -X POST -d "name=test" https://api.example.com

# With auth
curl -u user:pass https://api.example.com
```

---

## 📁 Files trong module này

| File | Mục đích |
|------|----------|
| [CHEATSHEET.md](./CHEATSHEET.md) | Tra cứu nhanh |
| [LABS.md](./LABS.md) | Bài thực hành |
| [QUIZ.md](./QUIZ.md) | Kiểm tra kiến thức |
| [EXERCISES.md](./EXERCISES.md) | Bài tập |
| [PROJECT.md](./PROJECT.md) | Mini project |
| [SOLUTIONS.md](./SOLUTIONS.md) | Đáp án |

---

## 🔗 Navigation

[⬅️ 1.2 Python](../1.2_Python_Basics/README.md) | [📚 Track 1](../README.md) | [1.4 Git ➡️](../1.4_Git_GitLab/README.md)

---

*Cập nhật: 2025-12-29*
