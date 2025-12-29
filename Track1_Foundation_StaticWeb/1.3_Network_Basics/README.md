# 🌐 Module 1.3: Network Basics

[![Duration](https://img.shields.io/badge/Duration-8--10%20hours-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Beginner-green?style=flat-square)](.)

> **Understanding Networks** - The foundation for all distributed systems.
>
> *Hiểu về mạng - Nền tảng cho mọi hệ thống phân tán.*

---

## 🎯 Learning Objectives (Mục tiêu học tập)

- [ ] Understand OSI and TCP/IP models (Hiểu mô hình OSI và TCP/IP)
- [ ] Understand IP addressing and subnetting (Hiểu địa chỉ IP và chia subnet)
- [ ] Understand DNS and how it works (Hiểu DNS và cách hoạt động)
- [ ] Use network troubleshooting tools (Sử dụng các công cụ khắc phục sự cố mạng)
- [ ] Understand HTTP/HTTPS protocol (Hiểu giao thức HTTP/HTTPS)

---

## 📋 Prerequisites (Điều kiện tiên quyết)

- Complete Module 1.2 (Hoàn thành Module 1.2)

---

## 📚 Content (Nội dung)

### 1. OSI and TCP/IP Models (Mô hình OSI và TCP/IP)

```
┌─────────────────────────────────────────────────────────────┐
│       OSI Model           │       TCP/IP Model              │
├───────────────────────────┼─────────────────────────────────┤
│ 7. Application            │                                 │
│ 6. Presentation           │    4. Application               │
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

### 2. IP Addressing (Địa chỉ IP)

#### IPv4 Format (Định dạng IPv4)

```
192.168.1.100
└─┬─┘ └┬┘ └┬┘ └┬┘
  │    │   │   └── Host (0-255)
  │    │   └────── Subnet
  │    └────────── Class B
  └─────────────── Class B
```

#### Important IP Ranges (Các dải IP quan trọng)

| Type (Loại) | Range (Dải) | Description (Mô tả) |
|-------------|-------------|---------------------|
| **Private** | 192.168.0.0/16 | Internal network - popular (Mạng nội bộ - phổ biến) |
| **Private** | 10.0.0.0/8 | Internal network - large (Mạng nội bộ - lớn) |
| **Private** | 172.16.0.0/12 | Internal network (Mạng nội bộ) |
| **Loopback** | 127.0.0.1 | Localhost |
| **Public** | All others (Còn lại) | Internet |

#### CIDR Notation (Ký hiệu CIDR)

| CIDR | Subnet Mask | Hosts |
|------|-------------|-------|
| /24 | 255.255.255.0 | 254 |
| /16 | 255.255.0.0 | 65,534 |
| /8 | 255.0.0.0 | 16,777,214 |

---

### 3. Ports and Protocols (Cổng và Giao thức)

#### Common Ports (Các cổng phổ biến)

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
| Connection-oriented (Hướng kết nối) | Connectionless (Không kết nối) |
| Reliable - retransmit (Đáng tin cậy) | Fast - no guarantee (Nhanh) |
| HTTP, SSH, SMTP | DNS, VoIP, Streaming |

---

### 4. DNS (Domain Name System - Hệ thống tên miền)

```
Browser request: www.example.com
          │
          ▼
   ┌──────────────┐
   │ Local Cache  │──► Found? Return IP (Tìm thấy? Trả về IP)
   └──────────────┘
          │
          ▼
   ┌──────────────┐
   │ DNS Resolver │ (ISP or 8.8.8.8)
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

#### DNS Record Types (Các loại bản ghi DNS)

| Record | Description (Mô tả) | Example (Ví dụ) |
|--------|---------------------|-----------------|
| **A** | Domain → IPv4 | example.com → 93.184.216.34 |
| **AAAA** | Domain → IPv6 | example.com → 2001:db8::1 |
| **CNAME** | Alias (Bí danh) | <www.example.com> → example.com |
| **MX** | Mail server | example.com → mail.example.com |
| **TXT** | Text info | SPF, DKIM records |

---

### 5. HTTP/HTTPS

#### HTTP Methods (Các phương thức HTTP)

| Method | Description (Mô tả) | Example (Ví dụ) |
|--------|---------------------|-----------------|
| GET | Retrieve data (Lấy dữ liệu) | View webpage (Xem trang web) |
| POST | Create new (Tạo mới) | Submit form (Gửi form) |
| PUT | Update entire (Cập nhật toàn bộ) | Update user info |
| PATCH | Update partial (Cập nhật một phần) | Change password (Đổi mật khẩu) |
| DELETE | Delete (Xóa) | Delete account (Xóa tài khoản) |

#### HTTP Status Codes (Mã trạng thái HTTP)

| Code | Meaning (Ý nghĩa) |
|------|-------------------|
| **2xx** | Success (Thành công) |
| 200 | OK |
| 201 | Created (Đã tạo) |
| **3xx** | Redirect (Chuyển hướng) |
| 301 | Moved Permanently (Di chuyển vĩnh viễn) |
| 302 | Found - Temporary (Tạm thời) |
| **4xx** | Client Error (Lỗi client) |
| 400 | Bad Request (Yêu cầu sai) |
| 401 | Unauthorized (Chưa xác thực) |
| 403 | Forbidden (Bị cấm) |
| 404 | Not Found (Không tìm thấy) |
| **5xx** | Server Error (Lỗi server) |
| 500 | Internal Server Error (Lỗi server nội bộ) |
| 502 | Bad Gateway (Gateway lỗi) |
| 503 | Service Unavailable (Dịch vụ không khả dụng) |

---

### 6. Network Troubleshooting Tools (Công cụ khắc phục sự cố mạng)

#### ping - Check connectivity (Kiểm tra kết nối)

```bash
ping google.com
ping -c 4 google.com    # Ping 4 times only (Chỉ ping 4 lần)

# Output:
# PING google.com (142.250.X.X): 56 data bytes
# 64 bytes from 142.250.X.X: icmp_seq=0 ttl=117 time=10.5 ms
```

#### traceroute - View packet route (Xem đường đi của packet)

```bash
traceroute google.com
tracert google.com      # Windows
```

#### nslookup - DNS lookup (Tra cứu DNS)

```bash
nslookup google.com
nslookup -type=MX google.com
```

#### dig - Advanced DNS lookup (Tra cứu DNS nâng cao)

```bash
dig google.com
dig google.com A
dig google.com MX
dig +short google.com
```

#### netstat - View connections (Xem các kết nối)

```bash
netstat -tulpn          # Linux: listening ports (Các cổng đang lắng nghe)
netstat -an             # All connections (Tất cả kết nối)
ss -tulpn               # Modern netstat (Netstat hiện đại)
```

#### curl - HTTP requests (Yêu cầu HTTP)

```bash
# GET request (Yêu cầu GET)
curl https://api.github.com

# View headers (Xem headers)
curl -I https://google.com

# POST request (Yêu cầu POST)
curl -X POST -d "name=test" https://api.example.com

# With auth (Với xác thực)
curl -u user:pass https://api.example.com
```

---

## 📝 Module Files (Các file trong Module)

| File | Description (Mô tả) |
|------|---------------------|
| [CHEATSHEET.md](./CHEATSHEET.md) | Quick reference (Tra cứu nhanh) |
| [LABS.md](./LABS.md) | Hands-on labs (Bài thực hành) |
| [QUIZ.md](./QUIZ.md) | Knowledge check (Kiểm tra kiến thức) |
| [EXERCISES.md](./EXERCISES.md) | Exercises (Bài tập) |
| [PROJECT.md](./PROJECT.md) | Mini project (Dự án nhỏ) |
| [SOLUTIONS.md](./SOLUTIONS.md) | Solutions (Đáp án) |

---

<div align="center">

### 🔗 Module Navigation (Điều hướng Module)

| ← Previous (Trước) | Current (Hiện tại) | Next (Tiếp) → |
|:------------------:|:------------------:|:-------------:|
| [1.2 Python](../1.2_Python_Basics/) | **1.3 Network** | [1.4 Git](../1.4_Git_GitLab/) |

---

**Master the network fundamentals! 🌐**

*Thành thạo kiến thức nền tảng về mạng!*

</div>
