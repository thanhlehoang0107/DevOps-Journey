# ❓ Quiz: Network Basics

> **Knowledge Check for Networking**
>
> *Kiểm tra kiến thức Networking. Chọn đáp án đúng nhất.*

---

## 📋 Instructions

- Tổng cộng: **20 câu hỏi**
- Thời gian: **15 phút**
- Passing score: **70% (14/20)**

---

## Questions

### Q1: OSI Model

Layer nào của OSI model chịu trách nhiệm cho routing?

a) Data Link Layer (2)  
b) Network Layer (3)  
c) Transport Layer (4)  
d) Session Layer (5)  

---

### Q2: TCP vs UDP

Protocol nào đảm bảo delivery và thứ tự của packets?

a) UDP  
b) TCP  
c) ICMP  
d) IP  

---

### Q3: Common Ports

Port nào được sử dụng cho SSH?

a) 21  
b) 22  
c) 23  
d) 25  

---

### Q4: HTTP Status

Status code 404 có nghĩa là gì?

a) Server Error  
b) Unauthorized  
c) Not Found  
d) Bad Request  

---

### Q5: IP Classes

IP address `172.16.5.10` thuộc class nào?

a) Class A  
b) Class B  
c) Class C  
d) Class D  

---

### Q6: CIDR Notation

CIDR `/24` tương đương với subnet mask nào?

a) 255.0.0.0  
b) 255.255.0.0  
c) 255.255.255.0  
d) 255.255.255.255  

---

### Q7: DNS

DNS chủ yếu sử dụng port nào?

a) 22  
b) 53  
c) 80  
d) 443  

---

### Q8: Private IP

Range nào KHÔNG phải private IP?

a) 10.0.0.0/8  
b) 172.16.0.0/12  
c) 192.168.0.0/16  
d) 169.254.0.0/16  

---

### Q9: HTTP Methods

HTTP method nào là idempotent?

a) POST  
b) GET  
c) PATCH  
d) Cả b và c  

---

### Q10: Network Command

Lệnh nào hiển thị routing table trên Linux?

a) route -n  
b) ip route  
c) netstat -r  
d) Tất cả đều đúng  

---

### Q11: SSL/TLS

Port mặc định cho HTTPS là gì?

a) 80  
b) 443  
c) 8080  
d) 8443  

---

### Q12: Firewall

Lệnh UFW nào cho phép incoming SSH?

a) `ufw allow 22`  
b) `ufw enable ssh`  
c) `ufw open ssh`  
d) `ufw permit 22`  

---

### Q13: DNS Records

Record type nào map domain name to IPv4 address?

a) AAAA  
b) A  
c) CNAME  
d) MX  

---

### Q14: TCP Handshake

TCP 3-way handshake bao gồm những bước nào?

a) SYN, ACK, FIN  
b) SYN, SYN-ACK, ACK  
c) ACK, SYN, FIN  
d) SYN, FIN, ACK  

---

### Q15: Ports

Lệnh nào hiển thị các ports đang listening?

a) `ss -tuln`  
b) `netstat -plant`  
c) `lsof -i`  
d) Tất cả đều đúng  

---

### Q16: CIDR Hosts

Một network `/26` có thể chứa bao nhiêu usable hosts?

a) 64  
b) 62  
c) 32  
d) 30  

---

### Q17: ARP

ARP protocol làm gì?

a) Map hostname to IP  
b) Map IP to MAC address  
c) Route packets  
d) Encrypt traffic  

---

### Q18: HTTP Status

Status code nào cho biết request thành công?

a) 100-199  
b) 200-299  
c) 300-399  
d) 400-499  

---

### Q19: Network Tools

Tool nào kết hợp ping và traceroute?

a) netstat  
b) mtr  
c) nmap  
d) tcpdump  

---

### Q20: Load Balancing

Layer 7 load balancer có thể route dựa trên?

a) IP address  
b) Port number  
c) HTTP headers  
d) Tất cả đều đúng  

---

## 📝 Answers

<details>
<summary><strong>Click để xem đáp án</strong></summary>

| Q | Answer | Explanation |
|---|--------|-------------|
| 1 | **b** | Network Layer (L3) handles routing via IP |
| 2 | **b** | TCP đảm bảo reliable, ordered delivery |
| 3 | **b** | SSH uses port 22 |
| 4 | **c** | 404 = Not Found |
| 5 | **b** | 172.16.x.x is Class B (128-191) |
| 6 | **c** | /24 = 255.255.255.0 |
| 7 | **b** | DNS uses port 53 |
| 8 | **d** | 169.254.x.x is link-local (APIPA), not private |
| 9 | **b** | GET is idempotent, POST và PATCH không |
| 10 | **d** | All commands show routing table |
| 11 | **b** | HTTPS default port is 443 |
| 12 | **a** | `ufw allow 22` or `ufw allow ssh` |
| 13 | **b** | A record = IPv4, AAAA = IPv6 |
| 14 | **b** | SYN → SYN-ACK → ACK |
| 15 | **d** | All show listening ports |
| 16 | **b** | /26 = 64 addresses - 2 (network + broadcast) = 62 |
| 17 | **b** | ARP maps IP to MAC address |
| 18 | **b** | 2xx codes indicate success |
| 19 | **b** | mtr = my traceroute |
| 20 | **d** | L7 can inspect all including application data |

### Scoring

- 18-20: Excellent! 🌟
- 14-17: Good! ✅
- 10-13: Need review 📚
- Below 10: Study more! 📖

</details>

---

**[← Back to README](./README.md)** | **[Go to Exercises →](./EXERCISES.md)**
