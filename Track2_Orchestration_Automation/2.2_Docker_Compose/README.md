# 🐳 Module 2.2: Docker Compose

[![Duration](https://img.shields.io/badge/Duration-1%20week-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Intermediate-orange?style=flat-square)](.)

> **Multi-container Orchestration** - Manage applications with Docker Compose.
>
> *Điều phối đa container - Quản lý ứng dụng với Docker Compose.*

---

## 🎯 Learning Objectives (Mục tiêu học tập)

After this module, you will (Sau module này, bạn sẽ):

- ✅ Write docker-compose.yml files (Viết docker-compose.yml)
- ✅ Manage multi-container applications (Quản lý ứng dụng đa container)
- ✅ Configure networks and volumes (Cấu hình mạng và volumes)
- ✅ Use environment variables and secrets (Sử dụng biến môi trường và secrets)
- ✅ Implement development workflows (Triển khai quy trình phát triển)
- ✅ Deploy with Compose in production (Deploy với Compose trong production)

---

## 📚 Content (Nội dung)

### 1. Docker Compose Basics (Cơ bản Docker Compose)

```yaml
# docker-compose.yml
version: '3.8'

services:
  web:
    image: nginx:alpine
    ports:
      - "80:80"
    volumes:
      - ./html:/usr/share/nginx/html
    
  api:
    build: ./api
    ports:
      - "3000:3000"
    environment:
      - NODE_ENV=development
    depends_on:
      - db
    
  db:
    image: postgres:15-alpine
    environment:
      POSTGRES_PASSWORD: secret
    volumes:
      - db-data:/var/lib/postgresql/data

volumes:
  db-data:
```

### Commands (Các lệnh)

```bash
docker compose up -d          # Start all services (Khởi động tất cả)
docker compose down           # Stop and remove (Dừng và xóa)
docker compose ps             # List services (Liệt kê services)
docker compose logs -f        # View logs (Xem logs)
docker compose exec api sh    # Exec into service (Vào service)
docker compose build          # Build images (Build images)
```

---

### 2. Service Configuration (Cấu hình Service)

```yaml
services:
  app:
    # Build from Dockerfile (Build từ Dockerfile)
    build:
      context: ./app
      dockerfile: Dockerfile
      args:
        - NODE_ENV=production
    
    # Or use image (Hoặc sử dụng image)
    image: myapp:latest
    
    # Container name (Tên container)
    container_name: myapp-container
    
    # Restart policy (Chính sách khởi động lại)
    restart: unless-stopped
    
    # Port mapping (Ánh xạ cổng)
    ports:
      - "3000:3000"
      - "3001:3001"
    
    # Environment (Biến môi trường)
    environment:
      - NODE_ENV=production
      - DB_HOST=db
    
    # Or from file (Hoặc từ file)
    env_file:
      - .env
      - .env.production
    
    # Dependencies (Phụ thuộc)
    depends_on:
      - db
      - cache
    
    # Health check (Kiểm tra sức khỏe)
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:3000/health"]
      interval: 30s
      timeout: 10s
      retries: 3
```

---

### 3. Networking (Mạng)

```yaml
version: '3.8'

services:
  frontend:
    networks:
      - frontend-network
  
  api:
    networks:
      - frontend-network
      - backend-network
  
  db:
    networks:
      - backend-network

networks:
  frontend-network:
    driver: bridge
  
  backend-network:
    driver: bridge
    internal: true  # No external access (Không truy cập từ bên ngoài)
```

---

### 4. Volumes

```yaml
services:
  db:
    volumes:
      # Named volume (Volume có tên)
      - db-data:/var/lib/postgresql/data
      
      # Bind mount (Mount trực tiếp)
      - ./init.sql:/docker-entrypoint-initdb.d/init.sql
      
      # Read-only bind mount (Mount chỉ đọc)
      - ./config:/etc/config:ro

volumes:
  db-data:
    driver: local
  
  # External volume - pre-created (Volume ngoài - tạo sẵn)
  logs:
    external: true
```

---

### 5. Environment Management (Quản lý môi trường)

```yaml
# .env file
POSTGRES_PASSWORD=mysecret
API_KEY=abc123

# docker-compose.yml
services:
  api:
    environment:
      - DB_PASSWORD=${POSTGRES_PASSWORD}
      - API_KEY=${API_KEY}
```

### Secrets (Swarm mode)

```yaml
services:
  api:
    secrets:
      - db_password

secrets:
  db_password:
    file: ./secrets/db_password.txt
```

---

### 6. Multiple Compose Files (Nhiều file Compose)

```yaml
# docker-compose.yml (base - cơ bản)
services:
  api:
    build: ./api
    ports:
      - "3000:3000"

# docker-compose.override.yml (development - phát triển)
services:
  api:
    volumes:
      - ./api:/app
    environment:
      - DEBUG=true

# docker-compose.prod.yml (production - sản xuất)
services:
  api:
    image: myregistry/api:latest
    deploy:
      replicas: 3
```

```bash
# Development - uses override automatically (Dev - tự động dùng override)
docker compose up

# Production (Sản xuất)
docker compose -f docker-compose.yml -f docker-compose.prod.yml up
```

---

### 7. Resource Limits (Giới hạn tài nguyên)

```yaml
services:
  api:
    deploy:
      resources:
        limits:
          cpus: '0.5'
          memory: 512M
        reservations:
          cpus: '0.25'
          memory: 256M
```

---

### 8. Logging (Ghi log)

```yaml
services:
  api:
    logging:
      driver: "json-file"
      options:
        max-size: "10m"
        max-file: "3"
```

---

## 📝 Module Files (Các file trong Module)

| File | Description |
|------|---------------------|
| [LABS.md](./LABS.md) | Hands-on labs (Bài thực hành) |
| [QUIZ.md](./QUIZ.md) | Knowledge check (Kiểm tra kiến thức) |
| [EXERCISES.md](./EXERCISES.md) | Practice exercises (Bài tập) |
| [PROJECT.md](./PROJECT.md) | Mini project (Dự án nhỏ) |
| [SOLUTIONS.md](./SOLUTIONS.md) | Solutions (Đáp án) |
| [CHEATSHEET.md](./CHEATSHEET.md) | Quick reference (Tra cứu nhanh) |

---

<div align="center">

### 🔗 Module Navigation (Điều hướng Module)

| ← Previous | Current | Next → |
|:------------------:|:------------------:|:-------------:|
| [2.1 Docker Advanced](../2.1_Docker_Advanced/) | **2.2 Docker Compose** | [2.3 Jenkins](../2.3_Jenkins/) |

---

**Master container orchestration! 🐳**

*Thành thạo điều phối container!*

</div>
