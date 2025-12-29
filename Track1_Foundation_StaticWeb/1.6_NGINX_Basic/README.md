# 🌐 Module 1.6: NGINX Basic

[![Duration](https://img.shields.io/badge/Duration-6--8%20hours-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Beginner-green?style=flat-square)](.)

> **Web Server and Reverse Proxy** - Serve static content and route traffic.
>
> *Web Server và Reverse Proxy - Serve nội dung tĩnh và điều hướng traffic.*

---

## 🎯 Learning Objectives (Mục tiêu học tập)

After this module, you will (Sau module này, bạn sẽ):

- ✅ Understand what NGINX is and its use cases (Hiểu NGINX là gì và use cases)
- ✅ Configure NGINX to serve static files (Cấu hình NGINX serve static files)
- ✅ Understand NGINX config file structure (Hiểu cấu trúc file config)
- ✅ Configure virtual hosts - server blocks (Cấu hình virtual hosts)
- ✅ Understand Reverse Proxy concept (Hiểu khái niệm Reverse Proxy)
- ✅ Deploy NGINX with Docker (Deploy NGINX với Docker)

---

## 📖 Nội dung

### 1. NGINX là gì? (30 phút)

#### 1.1 Giới thiệu

**NGINX** (đọc là "engine-x") là:

- 🌐 **Web Server**: Serve static files (HTML, CSS, JS, images)
- 🔄 **Reverse Proxy**: Điều hướng requests đến backend
- ⚖️ **Load Balancer**: Phân tải giữa nhiều servers
- 📦 **Cache**: Lưu cache responses

#### 1.2 NGINX vs Apache

| Tiêu chí | NGINX | Apache |
|----------|-------|--------|
| **Architecture** | Event-driven, async | Process/Thread per request |
| **Static content** | ✅ Rất nhanh | Chậm hơn |
| **Memory** | ✅ Ít RAM | Nhiều RAM hơn |
| **Concurrent connections** | ✅ Cao (10k+) | Giới hạn |
| **Config** | Đơn giản hơn | .htaccess linh hoạt |
| **Modules** | Compile time | Runtime |

#### 1.3 Use cases phổ biến

```
┌─────────────────────────────────────────────────────────────┐
│                    NGINX USE CASES                           │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  1. STATIC WEB SERVER                                        │
│     Browser → NGINX → HTML/CSS/JS/Images                    │
│                                                              │
│  2. REVERSE PROXY                                            │
│     Browser → NGINX → Backend (Node.js, Python, etc.)       │
│                                                              │
│  3. LOAD BALANCER                                            │
│     Browser → NGINX → Server1, Server2, Server3...          │
│                                                              │
│  4. SSL TERMINATION                                          │
│     Browser ─HTTPS→ NGINX ─HTTP→ Backend                    │
│                                                              │
│  5. API GATEWAY                                              │
│     Browser → NGINX → /api → API Server                     │
│                      → /    → Frontend Server               │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

---

### 2. Cài đặt và Chạy NGINX (1 giờ)

#### 2.1 Chạy với Docker (Khuyến nghị)

```bash
# Chạy NGINX container
docker run -d -p 80:80 --name nginx nginx:alpine

# Kiểm tra
curl http://localhost
# Hoặc mở browser: http://localhost

# Xem logs
docker logs nginx

# Vào terminal container
docker exec -it nginx sh
```

#### 2.2 Cài đặt trực tiếp (Optional)

```bash
# Ubuntu/Debian
sudo apt update
sudo apt install nginx
sudo systemctl start nginx
sudo systemctl enable nginx

# Kiểm tra status
sudo systemctl status nginx

# macOS với Homebrew
brew install nginx
brew services start nginx
```

#### 2.3 Kiểm tra cài đặt

```bash
# Kiểm tra version
nginx -v

# Kiểm tra config syntax
nginx -t

# Xem config đang dùng
nginx -T
```

---

### 3. Cấu trúc thư mục NGINX (30 phút)

#### 3.1 Thư mục quan trọng

```
/etc/nginx/                    # Config directory
├── nginx.conf                 # Main config file
├── conf.d/                    # Additional configs
│   └── default.conf           # Default server block
├── sites-available/           # Available site configs (Debian)
├── sites-enabled/             # Enabled sites (symlinks)
├── snippets/                  # Reusable config snippets
└── mime.types                 # MIME type mappings

/var/log/nginx/                # Logs
├── access.log                 # Access logs
└── error.log                  # Error logs

/usr/share/nginx/html/         # Default document root
└── index.html                 # Default welcome page
```

#### 3.2 Trong Docker Alpine

```bash
docker exec -it nginx sh

# Config
cat /etc/nginx/nginx.conf
ls /etc/nginx/conf.d/

# Web root
ls /usr/share/nginx/html/

# Logs
ls /var/log/nginx/
```

---

### 4. Cấu hình NGINX cơ bản (2 giờ)

#### 4.1 Cấu trúc file config

```nginx
# nginx.conf - Main config file

# Global context
user nginx;
worker_processes auto;
error_log /var/log/nginx/error.log warn;
pid /var/run/nginx.pid;

# Events context
events {
    worker_connections 1024;
}

# HTTP context
http {
    include /etc/nginx/mime.types;
    default_type application/octet-stream;

    # Logging format
    log_format main '$remote_addr - $remote_user [$time_local] '
                    '"$request" $status $body_bytes_sent '
                    '"$http_referer" "$http_user_agent"';

    access_log /var/log/nginx/access.log main;

    sendfile on;
    keepalive_timeout 65;

    # Include server blocks
    include /etc/nginx/conf.d/*.conf;
}
```

#### 4.2 Server Block (Virtual Host)

```nginx
# /etc/nginx/conf.d/default.conf

server {
    # Listen port
    listen 80;
    listen [::]:80;

    # Server name (domain)
    server_name localhost example.com www.example.com;

    # Document root
    root /usr/share/nginx/html;
    
    # Default file
    index index.html index.htm;

    # Location block
    location / {
        try_files $uri $uri/ =404;
    }
}
```

#### 4.3 Các directives quan trọng

| Directive | Mô tả | Ví dụ |
|-----------|-------|-------|
| `listen` | Port để lắng nghe | `listen 80;` |
| `server_name` | Domain name | `server_name example.com;` |
| `root` | Document root | `root /var/www/html;` |
| `index` | Default files | `index index.html;` |
| `location` | URL pattern matching | `location /api { }` |
| `try_files` | Try multiple files | `try_files $uri $uri/ =404;` |
| `error_page` | Custom error pages | `error_page 404 /404.html;` |

---

### 5. Serve Static Files (1 giờ)

#### 5.1 Basic Static Website

**Cấu trúc project:**

```
my-website/
├── docker-compose.yml
├── nginx.conf
└── html/
    ├── index.html
    ├── about.html
    ├── css/
    │   └── style.css
    ├── js/
    │   └── app.js
    └── images/
        └── logo.png
```

**nginx.conf:**

```nginx
server {
    listen 80;
    server_name localhost;
    root /usr/share/nginx/html;
    index index.html;

    # Serve static files
    location / {
        try_files $uri $uri/ =404;
    }

    # Cache static assets
    location ~* \.(css|js|jpg|jpeg|png|gif|ico|svg|woff|woff2)$ {
        expires 1y;
        add_header Cache-Control "public, immutable";
    }

    # Custom 404 page
    error_page 404 /404.html;
    location = /404.html {
        internal;
    }
}
```

**Dockerfile:**

```dockerfile
FROM nginx:alpine

# Copy custom config
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Copy website files
COPY html/ /usr/share/nginx/html/

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
```

#### 5.2 Gzip Compression

```nginx
http {
    # Enable gzip
    gzip on;
    gzip_vary on;
    gzip_min_length 1024;
    gzip_proxied expired no-cache no-store private auth;
    gzip_types text/plain text/css text/xml text/javascript 
               application/x-javascript application/xml 
               application/javascript application/json;
    gzip_disable "MSIE [1-6]\.";
}
```

---

### 6. Reverse Proxy (1.5 giờ)

#### 6.1 Khái niệm

```
┌─────────────────────────────────────────────────────────────┐
│                    REVERSE PROXY                             │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│   Client                                                     │
│     │                                                        │
│     ▼                                                        │
│  ┌─────────────────┐                                        │
│  │     NGINX       │  ← Proxy Server                        │
│  │  (Port 80/443)  │                                        │
│  └────────┬────────┘                                        │
│           │                                                  │
│     ┌─────┴─────┐                                           │
│     │           │                                           │
│     ▼           ▼                                           │
│  ┌──────┐   ┌──────┐                                        │
│  │ API  │   │ Web  │  ← Backend Servers                     │
│  │:3000 │   │:8080 │                                        │
│  └──────┘   └──────┘                                        │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

#### 6.2 Basic Reverse Proxy

```nginx
server {
    listen 80;
    server_name api.example.com;

    location / {
        proxy_pass http://backend:3000;
        
        # Headers quan trọng
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

#### 6.3 Multiple Backends

```nginx
server {
    listen 80;
    server_name example.com;

    # Frontend - Static files
    location / {
        root /usr/share/nginx/html;
        try_files $uri $uri/ /index.html;
    }

    # API - Proxy to backend
    location /api/ {
        proxy_pass http://api-server:3000/;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }

    # WebSocket support
    location /ws/ {
        proxy_pass http://ws-server:8080/;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
    }
}
```

---

### 7. Load Balancing Basics (1 giờ)

#### 7.1 Round Robin (Default)

```nginx
upstream backend {
    server backend1:3000;
    server backend2:3000;
    server backend3:3000;
}

server {
    listen 80;
    
    location / {
        proxy_pass http://backend;
    }
}
```

#### 7.2 Weighted Load Balancing

```nginx
upstream backend {
    server backend1:3000 weight=3;  # 3x traffic
    server backend2:3000 weight=1;  # 1x traffic
    server backend3:3000 weight=1;  # 1x traffic
}
```

#### 7.3 Health Checks

```nginx
upstream backend {
    server backend1:3000;
    server backend2:3000;
    server backend3:3000 backup;  # Only if others fail
    
    # Passive health check
    server backend4:3000 max_fails=3 fail_timeout=30s;
}
```

---

### 8. NGINX với Docker Compose (1 giờ)

#### 8.1 Full Stack Example

**docker-compose.yml:**

```yaml
version: '3.8'

services:
  nginx:
    image: nginx:alpine
    ports:
      - "80:80"
    volumes:
      - ./nginx.conf:/etc/nginx/conf.d/default.conf:ro
      - ./html:/usr/share/nginx/html:ro
    depends_on:
      - api
    networks:
      - app-network

  api:
    build: ./api
    expose:
      - "3000"
    environment:
      - NODE_ENV=production
    networks:
      - app-network

networks:
  app-network:
    driver: bridge
```

**nginx.conf:**

```nginx
server {
    listen 80;
    server_name localhost;

    # Serve static frontend
    location / {
        root /usr/share/nginx/html;
        index index.html;
        try_files $uri $uri/ /index.html;
    }

    # Proxy API requests
    location /api/ {
        proxy_pass http://api:3000/;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
```

---

### 9. Debugging và Logging (30 phút)

#### 9.1 Xem logs

```bash
# Docker
docker logs nginx
docker logs -f nginx

# Linux
sudo tail -f /var/log/nginx/access.log
sudo tail -f /var/log/nginx/error.log
```

#### 9.2 Custom log format

```nginx
http {
    log_format detailed '$remote_addr - $remote_user [$time_local] '
                        '"$request" $status $body_bytes_sent '
                        '"$http_referer" "$http_user_agent" '
                        '$request_time $upstream_response_time';
    
    access_log /var/log/nginx/access.log detailed;
}
```

#### 9.3 Debug tips

```bash
# Test config syntax
nginx -t

# Show full config
nginx -T

# Reload config (không downtime)
nginx -s reload

# Docker
docker exec nginx nginx -t
docker exec nginx nginx -s reload
```

---

### 10. Security Best Practices (30 phút)

```nginx
server {
    # Hide NGINX version
    server_tokens off;

    # Security headers
    add_header X-Frame-Options "SAMEORIGIN" always;
    add_header X-Content-Type-Options "nosniff" always;
    add_header X-XSS-Protection "1; mode=block" always;
    add_header Referrer-Policy "strict-origin-when-cross-origin" always;

    # Limit request size
    client_max_body_size 10M;

    # Rate limiting
    limit_req_zone $binary_remote_addr zone=mylimit:10m rate=10r/s;
    
    location /api/ {
        limit_req zone=mylimit burst=20 nodelay;
        proxy_pass http://backend;
    }

    # Block common attacks
    location ~* \.(git|svn|htaccess)$ {
        deny all;
    }
}
```

---

## 📝 Module Files (Các file trong Module)

| File | Description |
|------|-------------|
| [CHEATSHEET.md](./CHEATSHEET.md) | Quick reference (Tra cứu nhanh) |
| [LABS.md](./LABS.md) | Hands-on labs (Bài thực hành) |
| [QUIZ.md](./QUIZ.md) | Knowledge check (Kiểm tra kiến thức) |
| [EXERCISES.md](./EXERCISES.md) | Exercises (Bài tập) |
| [PROJECT.md](./PROJECT.md) | Mini project (Dự án nhỏ) |
| [SOLUTIONS.md](./SOLUTIONS.md) | Solutions (Đáp án) |

---

<div align="center">

### 🔗 Module Navigation (Điều hướng Module)

| ← Previous | Current | Next → |
|:------------------:|:------------------:|:-------------:|
| [1.5 Docker](../1.5_Docker_Fundamentals/) | **1.6 NGINX** | [1.7 CI/CD](../1.7_CICD_Basic/) |

---

**Master NGINX! 🌐**

*Thành thạo NGINX!*

</div>
