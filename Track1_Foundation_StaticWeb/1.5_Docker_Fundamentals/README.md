# 🐳 Module 1.5: Docker Fundamentals

> Containerization - Đóng gói ứng dụng một cách nhất quán

---

## 📋 Thông tin Module

| Thuộc tính | Giá trị |
|------------|---------|
| **Thời lượng** | 12-15 giờ |
| **Độ khó** | ⭐⭐ Beginner-Intermediate |
| **Yêu cầu trước** | Module 1.4 hoàn thành, Docker đã cài đặt |
| **Output** | Build và run Docker container cho ứng dụng |

---

## 🎯 Mục tiêu học tập

Sau khi hoàn thành module này, bạn sẽ:

- [ ] Hiểu Container là gì và khác VM như thế nào
- [ ] Hiểu Docker architecture (daemon, client, registry)
- [ ] Viết Dockerfile để build images
- [ ] Chạy, quản lý containers
- [ ] Sử dụng Docker volumes và networks
- [ ] Push images lên Docker Hub

---

## 📖 Nội dung

### 1. Container vs Virtual Machine (1 giờ)

#### 1.1 Virtual Machine

```
┌─────────────────────────────────────────────────────────────┐
│                    VIRTUAL MACHINES                          │
├─────────────────────────────────────────────────────────────┤
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐         │
│  │    App A    │  │    App B    │  │    App C    │         │
│  ├─────────────┤  ├─────────────┤  ├─────────────┤         │
│  │   Bins/Libs │  │   Bins/Libs │  │   Bins/Libs │         │
│  ├─────────────┤  ├─────────────┤  ├─────────────┤         │
│  │  Guest OS   │  │  Guest OS   │  │  Guest OS   │ ← Nặng! │
│  │  (Ubuntu)   │  │  (CentOS)   │  │  (Debian)   │         │
│  └─────────────┘  └─────────────┘  └─────────────┘         │
├─────────────────────────────────────────────────────────────┤
│                      HYPERVISOR                              │
├─────────────────────────────────────────────────────────────┤
│                      HOST OS                                 │
├─────────────────────────────────────────────────────────────┤
│                    INFRASTRUCTURE                            │
└─────────────────────────────────────────────────────────────┘
```

**Đặc điểm VM:**

- ✅ Isolation hoàn toàn
- ❌ Nặng (GB mỗi VM)
- ❌ Khởi động chậm (phút)
- ❌ Tốn tài nguyên

#### 1.2 Container

```
┌─────────────────────────────────────────────────────────────┐
│                      CONTAINERS                              │
├─────────────────────────────────────────────────────────────┤
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐         │
│  │    App A    │  │    App B    │  │    App C    │         │
│  ├─────────────┤  ├─────────────┤  ├─────────────┤         │
│  │   Bins/Libs │  │   Bins/Libs │  │   Bins/Libs │ ← Nhẹ! │
│  └─────────────┘  └─────────────┘  └─────────────┘         │
├─────────────────────────────────────────────────────────────┤
│                    DOCKER ENGINE                             │
├─────────────────────────────────────────────────────────────┤
│                      HOST OS                                 │
├─────────────────────────────────────────────────────────────┤
│                    INFRASTRUCTURE                            │
└─────────────────────────────────────────────────────────────┘
```

**Đặc điểm Container:**

- ✅ Nhẹ (MB)
- ✅ Khởi động nhanh (giây)
- ✅ Chia sẻ kernel với host
- ✅ Portable - chạy ở đâu cũng được

#### 1.3 So sánh

| Tiêu chí | VM | Container |
|----------|-----|-----------|
| **Kích thước** | GB | MB |
| **Khởi động** | Phút | Giây |
| **Isolation** | Hoàn toàn | Process level |
| **OS** | Riêng biệt | Chia sẻ kernel |
| **Density** | Ít VM/host | Nhiều container/host |
| **Use case** | Multi-tenant, legacy | Microservices, CI/CD |

---

### 2. Docker Architecture (1 giờ)

```
┌─────────────────────────────────────────────────────────────┐
│                    DOCKER ARCHITECTURE                       │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  ┌──────────────────┐                                       │
│  │   Docker Client  │  docker build, run, pull...          │
│  │   (CLI / API)    │                                       │
│  └────────┬─────────┘                                       │
│           │ REST API                                         │
│           ▼                                                  │
│  ┌──────────────────┐                                       │
│  │   Docker Daemon  │  dockerd                              │
│  │   (Docker Host)  │                                       │
│  ├──────────────────┤                                       │
│  │  ┌────────────┐  │                                       │
│  │  │  Images    │  │  ← Blueprints                        │
│  │  └────────────┘  │                                       │
│  │  ┌────────────┐  │                                       │
│  │  │ Containers │  │  ← Running instances                 │
│  │  └────────────┘  │                                       │
│  │  ┌────────────┐  │                                       │
│  │  │  Volumes   │  │  ← Persistent data                   │
│  │  └────────────┘  │                                       │
│  │  ┌────────────┐  │                                       │
│  │  │  Networks  │  │  ← Container communication           │
│  │  └────────────┘  │                                       │
│  └──────────────────┘                                       │
│           │                                                  │
│           ▼                                                  │
│  ┌──────────────────┐                                       │
│  │  Docker Registry │  Docker Hub, ECR, GCR...             │
│  │  (Image storage) │                                       │
│  └──────────────────┘                                       │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

#### Các thành phần chính

| Component | Mô tả |
|-----------|-------|
| **Docker Client** | CLI bạn dùng (`docker run`, `docker build`) |
| **Docker Daemon** | Service chạy ngầm, quản lý containers |
| **Docker Image** | Template read-only, chứa app + dependencies |
| **Docker Container** | Instance đang chạy của image |
| **Docker Registry** | Nơi lưu trữ images (Docker Hub) |

---

### 3. Docker Images (2 giờ)

#### 3.1 Khái niệm Image

**Image** = Read-only template chứa:

- Base OS (Alpine, Ubuntu, Debian...)
- Application code
- Dependencies (libs, packages)
- Configuration

```
┌─────────────────────────────────────────┐
│           Docker Image Layers           │
├─────────────────────────────────────────┤
│  Layer 5: COPY app.js /app/             │ ← Your code
├─────────────────────────────────────────┤
│  Layer 4: RUN npm install               │ ← Dependencies
├─────────────────────────────────────────┤
│  Layer 3: WORKDIR /app                  │
├─────────────────────────────────────────┤
│  Layer 2: RUN apt-get update            │
├─────────────────────────────────────────┤
│  Layer 1: FROM node:18-alpine           │ ← Base image
└─────────────────────────────────────────┘
```

#### 3.2 Image naming convention

```
[registry/]repository[:tag]

Ví dụ:
nginx                          # Docker Hub, latest tag
nginx:alpine                   # Docker Hub, alpine tag
nginx:1.25.3                   # Specific version
myuser/myapp:v1.0              # User repository
gcr.io/project/app:latest      # Google Container Registry
123456789.dkr.ecr.region.amazonaws.com/app:v1  # AWS ECR
```

#### 3.3 Pull images

```bash
# Pull image từ Docker Hub
docker pull nginx
docker pull nginx:alpine
docker pull nginx:1.25.3

# Xem images đã pull
docker images
docker image ls

# Xem chi tiết image
docker image inspect nginx

# Xem history/layers
docker history nginx
```

#### 3.4 Xóa images

```bash
# Xóa 1 image
docker rmi nginx
docker image rm nginx

# Xóa nhiều images
docker rmi nginx redis mysql

# Xóa all unused images
docker image prune

# Xóa all images (nguy hiểm!)
docker rmi $(docker images -q)
```

---

### 4. Docker Containers (3 giờ)

#### 4.1 Chạy container

```bash
# Chạy container đơn giản
docker run nginx

# Chạy trong background (detached)
docker run -d nginx

# Đặt tên cho container
docker run -d --name my-nginx nginx

# Map port (host:container)
docker run -d -p 8080:80 nginx
# Truy cập: http://localhost:8080

# Map nhiều ports
docker run -d -p 8080:80 -p 8443:443 nginx

# Chạy với environment variables
docker run -d -e MYSQL_ROOT_PASSWORD=secret mysql

# Tự động xóa khi dừng
docker run --rm -it alpine sh
```

#### 4.2 Quản lý containers

```bash
# Liệt kê containers đang chạy
docker ps

# Liệt kê tất cả (kể cả đã dừng)
docker ps -a

# Dừng container
docker stop my-nginx
docker stop container_id

# Start container đã dừng
docker start my-nginx

# Restart container
docker restart my-nginx

# Xóa container (phải stop trước)
docker rm my-nginx

# Force remove (đang chạy)
docker rm -f my-nginx

# Xóa all stopped containers
docker container prune
```

#### 4.3 Tương tác với container

```bash
# Xem logs
docker logs my-nginx
docker logs -f my-nginx         # Follow mode
docker logs --tail 100 my-nginx # 100 dòng cuối

# Vào terminal của container
docker exec -it my-nginx bash
docker exec -it my-nginx sh     # Nếu không có bash

# Chạy lệnh trong container
docker exec my-nginx cat /etc/nginx/nginx.conf

# Copy files
docker cp local_file.txt my-nginx:/path/in/container/
docker cp my-nginx:/path/in/container/file.txt ./local/

# Xem stats (CPU, Memory)
docker stats
docker stats my-nginx
```

#### 4.4 Container lifecycle

```
┌─────────────────────────────────────────────────────────────┐
│                CONTAINER LIFECYCLE                           │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│       docker create                                          │
│            │                                                 │
│            ▼                                                 │
│     ┌──────────────┐                                        │
│     │   CREATED    │                                        │
│     └──────┬───────┘                                        │
│            │ docker start                                    │
│            ▼                                                 │
│     ┌──────────────┐  docker pause   ┌──────────────┐      │
│     │   RUNNING    │ ──────────────► │    PAUSED    │      │
│     └──────┬───────┘ ◄────────────── └──────────────┘      │
│            │          docker unpause                         │
│            │ docker stop                                     │
│            ▼                                                 │
│     ┌──────────────┐                                        │
│     │   STOPPED    │                                        │
│     └──────┬───────┘                                        │
│            │ docker rm                                       │
│            ▼                                                 │
│     ┌──────────────┐                                        │
│     │   DELETED    │                                        │
│     └──────────────┘                                        │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

---

### 5. Dockerfile (3 giờ)

#### 5.1 Dockerfile là gì?

**Dockerfile** = Text file chứa instructions để build Docker image

#### 5.2 Cấu trúc cơ bản

```dockerfile
# Syntax
# INSTRUCTION arguments

# Comment bắt đầu bằng #

FROM base_image          # Base image (BẮT BUỘC)
WORKDIR /app             # Set working directory
COPY source dest         # Copy files từ host vào image
RUN command              # Chạy command khi build
EXPOSE port              # Document port (không mở port)
ENV KEY=value            # Set environment variable
CMD ["executable"]       # Command mặc định khi run
```

#### 5.3 Các instructions quan trọng

| Instruction | Mô tả | Ví dụ |
|-------------|-------|-------|
| `FROM` | Base image | `FROM node:18-alpine` |
| `WORKDIR` | Set working directory | `WORKDIR /app` |
| `COPY` | Copy files từ host | `COPY . .` |
| `ADD` | Copy + extract archives | `ADD app.tar.gz /app` |
| `RUN` | Chạy command (build time) | `RUN npm install` |
| `CMD` | Default command (run time) | `CMD ["node", "app.js"]` |
| `ENTRYPOINT` | Fixed command | `ENTRYPOINT ["python"]` |
| `EXPOSE` | Document port | `EXPOSE 3000` |
| `ENV` | Environment variable | `ENV NODE_ENV=production` |
| `ARG` | Build-time variable | `ARG VERSION=1.0` |
| `VOLUME` | Mount point | `VOLUME /data` |
| `USER` | Set user | `USER node` |

#### 5.4 Ví dụ: Node.js Application

**Cấu trúc project:**

```
my-app/
├── Dockerfile
├── package.json
├── package-lock.json
└── src/
    └── app.js
```

**Dockerfile:**

```dockerfile
# 1. Base image
FROM node:18-alpine

# 2. Set working directory
WORKDIR /app

# 3. Copy package files first (cache optimization)
COPY package*.json ./

# 4. Install dependencies
RUN npm ci --only=production

# 5. Copy source code
COPY src/ ./src/

# 6. Expose port (documentation)
EXPOSE 3000

# 7. Set non-root user (security)
USER node

# 8. Default command
CMD ["node", "src/app.js"]
```

**Build và run:**

```bash
# Build image
docker build -t my-node-app .
docker build -t my-node-app:v1.0 .

# Run container
docker run -d -p 3000:3000 --name app my-node-app
```

#### 5.5 Ví dụ: Python Application

```dockerfile
FROM python:3.11-slim

WORKDIR /app

# Install dependencies first (cache)
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy source
COPY . .

EXPOSE 5000

# Use gunicorn for production
CMD ["gunicorn", "--bind", "0.0.0.0:5000", "app:app"]
```

#### 5.6 Ví dụ: Static Website với NGINX

```dockerfile
FROM nginx:alpine

# Copy static files
COPY ./html /usr/share/nginx/html

# Copy custom config (optional)
COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 80

# nginx runs as daemon by default
CMD ["nginx", "-g", "daemon off;"]
```

#### 5.7 Best Practices

```dockerfile
# ❌ BAD - Mỗi RUN tạo 1 layer
RUN apt-get update
RUN apt-get install -y curl
RUN apt-get install -y git
RUN apt-get clean

# ✅ GOOD - Gộp lại 1 layer
RUN apt-get update && apt-get install -y \
    curl \
    git \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
```

```dockerfile
# ❌ BAD - Copy all rồi mới install
COPY . .
RUN npm install

# ✅ GOOD - Copy package.json trước để tận dụng cache
COPY package*.json ./
RUN npm install
COPY . .
```

```dockerfile
# ✅ GOOD - Sử dụng .dockerignore
# File: .dockerignore
node_modules
.git
*.log
.env
Dockerfile
.dockerignore
```

---

### 6. Docker Volumes (2 giờ)

#### 6.1 Vấn đề: Data trong container

- Container bị xóa → Data mất
- Cần lưu data persistent

#### 6.2 Các loại mounts

```
┌─────────────────────────────────────────────────────────────┐
│                    DOCKER STORAGE                            │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  1. VOLUMES (Docker managed)                                 │
│     /var/lib/docker/volumes/my-vol/_data                    │
│                                                              │
│  2. BIND MOUNTS (Host path)                                  │
│     /home/user/data → /app/data                             │
│                                                              │
│  3. TMPFS (Memory only)                                      │
│     RAM → /app/cache                                         │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

#### 6.3 Volumes

```bash
# Tạo volume
docker volume create my-data

# Liệt kê volumes
docker volume ls

# Inspect volume
docker volume inspect my-data

# Sử dụng volume
docker run -d \
    -v my-data:/var/lib/mysql \
    --name mysql \
    mysql

# Xóa volume
docker volume rm my-data

# Xóa unused volumes
docker volume prune
```

#### 6.4 Bind Mounts

```bash
# Mount folder từ host
docker run -d \
    -v $(pwd)/data:/app/data \
    --name app \
    my-app

# Windows PowerShell
docker run -d `
    -v ${PWD}/data:/app/data `
    --name app `
    my-app

# Read-only mount
docker run -d \
    -v $(pwd)/config:/app/config:ro \
    my-app
```

#### 6.5 Use cases

| Use case | Loại mount | Ví dụ |
|----------|------------|-------|
| Database data | Volume | MySQL, PostgreSQL data |
| Development | Bind mount | Live reload code |
| Config files | Bind mount (ro) | nginx.conf |
| Logs | Volume hoặc Bind | application logs |
| Secrets | tmpfs | Passwords, tokens |

---

### 7. Docker Networks (2 giờ)

#### 7.1 Network Types

| Driver | Mô tả | Use case |
|--------|-------|----------|
| **bridge** | Default, isolated network | Single host, dev |
| **host** | Use host network directly | Performance |
| **none** | No networking | Security |
| **overlay** | Multi-host network | Swarm, K8s |

#### 7.2 Bridge Network (Default)

```bash
# Tạo network
docker network create my-network

# Liệt kê networks
docker network ls

# Inspect network
docker network inspect my-network

# Chạy container trong network
docker run -d --name web --network my-network nginx
docker run -d --name api --network my-network my-api

# Containers có thể gọi nhau bằng tên
# Từ web: curl http://api:3000

# Xóa network
docker network rm my-network
```

#### 7.3 Container Communication

```bash
# Ví dụ: Web + API + Database

# 1. Tạo network
docker network create app-network

# 2. Database
docker run -d \
    --name db \
    --network app-network \
    -e POSTGRES_PASSWORD=secret \
    postgres

# 3. API (connect to db)
docker run -d \
    --name api \
    --network app-network \
    -e DATABASE_URL=postgresql://postgres:secret@db:5432/app \
    my-api

# 4. Web (connect to api)
docker run -d \
    --name web \
    --network app-network \
    -p 80:80 \
    -e API_URL=http://api:3000 \
    my-web
```

---

### 8. Docker Hub (1 giờ)

#### 8.1 Login

```bash
docker login
# Enter username and password
```

#### 8.2 Push image

```bash
# Tag image với username
docker tag my-app:v1.0 username/my-app:v1.0

# Push
docker push username/my-app:v1.0

# Push latest
docker tag my-app:v1.0 username/my-app:latest
docker push username/my-app:latest
```

#### 8.3 Pull image

```bash
docker pull username/my-app:v1.0
```

---

### 9. Thực hành: Deploy Static Website

#### Project Structure

```
my-website/
├── Dockerfile
├── nginx.conf
└── html/
    ├── index.html
    ├── css/
    │   └── style.css
    └── js/
        └── app.js
```

#### index.html

```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DevOps Journey</title>
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <h1>🚀 Welcome to DevOps Journey!</h1>
    <p>This website is running in a Docker container.</p>
    <p id="time"></p>
    <script src="js/app.js"></script>
</body>
</html>
```

#### Dockerfile

```dockerfile
FROM nginx:alpine

# Copy website files
COPY html/ /usr/share/nginx/html/

# Expose port
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]
```

#### Build và Run

```bash
# Build
docker build -t my-website:v1.0 .

# Run
docker run -d -p 8080:80 --name website my-website:v1.0

# Access: http://localhost:8080
```

---

## 📁 Files trong module này

| File | Mục đích |
|------|----------|
| [CHEATSHEET.md](./CHEATSHEET.md) | Tra cứu nhanh Docker |
| [LABS.md](./LABS.md) | Bài thực hành hands-on |
| [QUIZ.md](./QUIZ.md) | Kiểm tra kiến thức |
| [EXERCISES.md](./EXERCISES.md) | Bài tập tình huống |
| [PROJECT.md](./PROJECT.md) | Mini project |
| [SOLUTIONS.md](./SOLUTIONS.md) | Đáp án |

---

## 🎓 Tiếp theo

Sau khi hoàn thành module này, bạn đã biết cách containerize ứng dụng. Tiếp tục với:

**[➡️ Module 1.6: NGINX Basic](../1.6_NGINX_Basic/README.md)**

---

## 🔗 Navigation

[⬅️ 1.4 Git & GitHub](../1.4_Git_GitLab/README.md) | [📚 Track 1](../README.md) | [1.6 NGINX Basic ➡️](../1.6_NGINX_Basic/README.md)

---

*Cập nhật: 2025-12-29*
