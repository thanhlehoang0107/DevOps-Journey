# 🐳 Module 2.2: Docker Compose

[![Duration](https://img.shields.io/badge/Duration-1%20week-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Intermediate-orange?style=flat-square)](.)

> **Multi-container orchestration** - Quản lý applications với Docker Compose.

---

## 🎯 Learning Objectives

Sau module này, bạn sẽ:

- ✅ Viết docker-compose.yml files
- ✅ Quản lý multi-container applications
- ✅ Configure networks và volumes
- ✅ Use environment variables và secrets
- ✅ Implement development workflows
- ✅ Deploy với Compose in production

---

## 📚 Content

### 1. Docker Compose Basics

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

### Commands

```bash
docker compose up -d          # Start all services
docker compose down           # Stop and remove
docker compose ps             # List services
docker compose logs -f        # View logs
docker compose exec api sh    # Exec into service
docker compose build          # Build images
```

---

### 2. Service Configuration

```yaml
services:
  app:
    # Build from Dockerfile
    build:
      context: ./app
      dockerfile: Dockerfile
      args:
        - NODE_ENV=production
    
    # Or use image
    image: myapp:latest
    
    # Container name
    container_name: myapp-container
    
    # Restart policy
    restart: unless-stopped
    
    # Port mapping
    ports:
      - "3000:3000"
      - "3001:3001"
    
    # Environment
    environment:
      - NODE_ENV=production
      - DB_HOST=db
    
    # Or from file
    env_file:
      - .env
      - .env.production
    
    # Dependencies
    depends_on:
      - db
      - cache
    
    # Health check
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:3000/health"]
      interval: 30s
      timeout: 10s
      retries: 3
```

---

### 3. Networking

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
    internal: true  # No external access
```

---

### 4. Volumes

```yaml
services:
  db:
    volumes:
      # Named volume
      - db-data:/var/lib/postgresql/data
      
      # Bind mount
      - ./init.sql:/docker-entrypoint-initdb.d/init.sql
      
      # Read-only bind mount
      - ./config:/etc/config:ro

volumes:
  db-data:
    driver: local
  
  # External volume (pre-created)
  logs:
    external: true
```

---

### 5. Environment Management

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

### 6. Multiple Compose Files

```yaml
# docker-compose.yml (base)
services:
  api:
    build: ./api
    ports:
      - "3000:3000"

# docker-compose.override.yml (development)
services:
  api:
    volumes:
      - ./api:/app
    environment:
      - DEBUG=true

# docker-compose.prod.yml (production)
services:
  api:
    image: myregistry/api:latest
    deploy:
      replicas: 3
```

```bash
# Development (uses override automatically)
docker compose up

# Production
docker compose -f docker-compose.yml -f docker-compose.prod.yml up
```

---

### 7. Resource Limits

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

### 8. Logging

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

## 🔗 Module Navigation

| Previous | Current | Next |
|----------|---------|------|
| [2.1 Docker Advanced](../2.1_Docker_Advanced/) | **2.2 Docker Compose** | [2.3 Jenkins](../2.3_Jenkins/) |

---

## 📝 Module Files

| File | Description |
|------|-------------|
| [LABS.md](./LABS.md) | Hands-on labs |
| [QUIZ.md](./QUIZ.md) | Knowledge check |
| [EXERCISES.md](./EXERCISES.md) | Practice exercises |
| [PROJECT.md](./PROJECT.md) | Mini project |
| [SOLUTIONS.md](./SOLUTIONS.md) | Solutions |
| [CHEATSHEET.md](./CHEATSHEET.md) | Quick reference |
