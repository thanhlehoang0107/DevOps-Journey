# 🔬 Labs: Network Basics

> Bài thực hành về networking cho DevOps.

---

## 🔬 Lab 1: IP Configuration

### Objectives

- Xem và hiểu IP configuration
- Làm việc với network interfaces

### Steps

#### Step 1: View IP Addresses

```bash
# Method 1: ip command (modern)
ip addr show

# Method 2: ifconfig (legacy)
ifconfig

# View specific interface
ip addr show eth0
```

#### Step 2: Understand Output

```
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500
    link/ether 00:11:22:33:44:55 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.100/24 brd 192.168.1.255 scope global eth0
    inet6 fe80::1 scope link
```

- `inet 192.168.1.100/24` - IPv4 address với CIDR
- `link/ether` - MAC address
- `mtu 1500` - Maximum Transmission Unit
- `UP,LOWER_UP` - Interface is active

#### Step 3: View Routing Table

```bash
ip route show

# Example output:
# default via 192.168.1.1 dev eth0
# 192.168.1.0/24 dev eth0 proto kernel scope link src 192.168.1.100
```

---

## 🔬 Lab 2: DNS Resolution

### Objectives

- Hiểu DNS resolution
- Sử dụng các công cụ DNS

### Steps

#### Step 1: Check DNS Configuration

```bash
cat /etc/resolv.conf
```

#### Step 2: DNS Lookup với nslookup

```bash
# Basic lookup
nslookup google.com

# Query specific DNS server
nslookup google.com 8.8.8.8

# Reverse lookup
nslookup 142.250.190.14
```

#### Step 3: DNS Lookup với dig

```bash
# Basic query
dig google.com

# Query specific record types
dig google.com A        # IPv4 address
dig google.com AAAA     # IPv6 address
dig google.com MX       # Mail servers
dig google.com NS       # Name servers
dig google.com TXT      # Text records

# Short output
dig +short google.com

# Trace DNS resolution
dig +trace google.com
```

#### Step 4: Check Local DNS Cache

```bash
# View /etc/hosts
cat /etc/hosts

# Add custom entry
echo "192.168.1.100 myserver" | sudo tee -a /etc/hosts
```

---

## 🔬 Lab 3: Connectivity Testing

### Objectives

- Test network connectivity
- Diagnose network issues

### Steps

#### Step 1: Ping Tests

```bash
# Ping local gateway
ip route | grep default
ping -c 4 192.168.1.1

# Ping external IP
ping -c 4 8.8.8.8

# Ping hostname
ping -c 4 google.com

# Continuous ping
ping google.com

# With timestamp
ping -D google.com
```

#### Step 2: Traceroute

```bash
# Trace route to destination
traceroute google.com

# Using ICMP (if UDP blocked)
traceroute -I google.com

# Using TCP
traceroute -T -p 443 google.com
```

#### Step 3: MTR (My TraceRoute)

```bash
# Install if needed
sudo apt install mtr

# Run MTR
mtr google.com

# Report mode
mtr -r -c 10 google.com
```

---

## 🔬 Lab 4: Port Scanning and Testing

### Objectives

- Check open ports
- Test port connectivity

### Steps

#### Step 1: Check Local Listening Ports

```bash
# Using ss (modern)
ss -tuln

# Breakdown:
# -t: TCP
# -u: UDP
# -l: Listening
# -n: Numeric (don't resolve names)

# With process info (requires root)
sudo ss -tulnp
```

#### Step 2: Test Remote Port

```bash
# Using netcat
nc -zv google.com 443
nc -zv google.com 80

# Using telnet
telnet google.com 80

# Using curl
curl -v telnet://google.com:443
```

#### Step 3: Port Scanning with nmap

```bash
# Install if needed
sudo apt install nmap

# Scan common ports
nmap localhost

# Scan specific ports
nmap -p 22,80,443 google.com

# Scan range
nmap -p 1-1000 localhost

# Service detection
nmap -sV localhost
```

---

## 🔬 Lab 5: HTTP Testing with cURL

### Objectives

- Make HTTP requests
- Understand HTTP headers và responses

### Steps

#### Step 1: Basic Requests

```bash
# GET request
curl https://httpbin.org/get

# POST request
curl -X POST https://httpbin.org/post

# With data
curl -X POST -d "name=test&value=123" https://httpbin.org/post

# With JSON
curl -X POST \
  -H "Content-Type: application/json" \
  -d '{"name":"test","value":123}' \
  https://httpbin.org/post
```

#### Step 2: Headers and Response

```bash
# Show response headers
curl -I https://httpbin.org/get

# Show both request and response headers
curl -v https://httpbin.org/get

# Add custom headers
curl -H "Authorization: Bearer mytoken" \
     -H "X-Custom-Header: value" \
     https://httpbin.org/headers
```

#### Step 3: Follow Redirects and Timeouts

```bash
# Follow redirects
curl -L http://google.com

# Set timeout
curl --connect-timeout 5 --max-time 10 https://httpbin.org/delay/3

# Save response to file
curl -o response.json https://httpbin.org/get
```

---

## 🔬 Lab 6: Firewall Configuration

### Objectives

- Configure firewall rules
- Understand traffic filtering

### Steps (UFW - Ubuntu)

#### Step 1: Check Status

```bash
sudo ufw status verbose
```

#### Step 2: Basic Configuration

```bash
# Enable firewall
sudo ufw enable

# Set default policies
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

#### Step 3: Allow Services

```bash
# Allow SSH
sudo ufw allow ssh
# or
sudo ufw allow 22/tcp

# Allow HTTP/HTTPS
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp

# Allow from specific IP
sudo ufw allow from 192.168.1.0/24

# Allow to specific port from IP
sudo ufw allow from 192.168.1.100 to any port 22
```

#### Step 4: View and Manage Rules

```bash
# View numbered rules
sudo ufw status numbered

# Delete rule
sudo ufw delete 2
# or
sudo ufw delete allow 80/tcp

# Reset all rules
sudo ufw reset
```

---

## 🔬 Lab 7: Network Troubleshooting

### Objectives

- Diagnose network problems
- Apply troubleshooting methodology

### Scenario

Cannot access website `example.com`

### Steps

#### Step 1: Check Local Network

```bash
# Check interface is up
ip link show

# Check IP address
ip addr show

# Check default gateway
ip route | grep default
```

#### Step 2: Test Gateway Connectivity

```bash
# Ping gateway
ping -c 4 $(ip route | grep default | awk '{print $3}')
```

#### Step 3: Test DNS

```bash
# Check DNS server
cat /etc/resolv.conf

# Test DNS resolution
nslookup example.com
dig example.com

# Try alternative DNS
nslookup example.com 8.8.8.8
```

#### Step 4: Test External Connectivity

```bash
# Ping external IP (bypasses DNS)
ping -c 4 8.8.8.8

# If that works, DNS is likely the issue
# If fails, routing or firewall issue
```

#### Step 5: Test HTTP

```bash
# Test with curl
curl -v https://example.com

# Check if port is blocked
nc -zv example.com 443
```

#### Step 6: Check Firewall

```bash
sudo ufw status
sudo iptables -L -n
```

---

## 🔬 Lab 8: SSL/TLS Certificates

### Objectives

- Understand SSL certificates
- Check and verify certificates

### Steps

#### Step 1: View Remote Certificate

```bash
# Connect and show certificate
openssl s_client -connect google.com:443 </dev/null

# Get just the certificate
echo | openssl s_client -connect google.com:443 2>/dev/null | \
  openssl x509 -noout -text
```

#### Step 2: Check Certificate Details

```bash
# Expiration date
echo | openssl s_client -connect google.com:443 2>/dev/null | \
  openssl x509 -noout -dates

# Subject and issuer
echo | openssl s_client -connect google.com:443 2>/dev/null | \
  openssl x509 -noout -subject -issuer

# All certificate information
echo | openssl s_client -connect google.com:443 2>/dev/null | \
  openssl x509 -noout -text | head -30
```

#### Step 3: Generate Self-signed Certificate

```bash
# Generate key and certificate
openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
  -keyout server.key \
  -out server.crt \
  -subj "/C=US/ST=State/L=City/O=Org/CN=localhost"

# View generated certificate
openssl x509 -in server.crt -text -noout
```

---

## ✅ Lab Completion Checklist

- [ ] Lab 1: IP Configuration
- [ ] Lab 2: DNS Resolution
- [ ] Lab 3: Connectivity Testing
- [ ] Lab 4: Port Scanning
- [ ] Lab 5: HTTP with cURL
- [ ] Lab 6: Firewall Configuration
- [ ] Lab 7: Troubleshooting
- [ ] Lab 8: SSL/TLS

---

**[← Back to README](./README.md)** | **[Go to Quiz →](./QUIZ.md)**
