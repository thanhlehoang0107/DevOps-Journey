# 🐳 Module 2.1: Docker Advanced

[![Duration](https://img.shields.io/badge/Duration-1%20week-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Intermediate-orange?style=flat-square)](.)

> **Advanced Docker Skills** - Multi-stage builds, optimization, and security best practices.
>
> *Nâng cao kỹ năng Docker - Multi-stage builds, tối ưu hóa, và bảo mật.*

---

## 🎯 Learning Objectives (Mục tiêu học tập)

After this module, you will (Sau module này, bạn sẽ):

- ✅ Master multi-stage builds (Thành thạo multi-stage builds)
- ✅ Optimize Docker images - size, layers, caching (Tối ưu Docker images)
- ✅ Implement Docker security best practices (Áp dụng bảo mật Docker)
- ✅ Use BuildKit advanced features (Sử dụng tính năng BuildKit)
- ✅ Debug and troubleshoot containers (Debug và xử lý sự cố)
- ✅ Understand Docker internals (Hiểu cơ chế bên trong Docker)

---

## 📋 Prerequisites (Điều kiện tiên quyết)

- Complete Track 1, especially module 1.5 Docker Fundamentals (Hoàn thành Track 1)
- Docker Desktop installed (Đã cài Docker Desktop)
- Understand Dockerfile basics (Hiểu Dockerfile cơ bản)

---

## 📚 Content (Nội dung)

### 1. Multi-stage Builds

#### Basic Multi-stage

```dockerfile
# Stage 1: Build
FROM node:18 AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

# Stage 2: Production
FROM node:18-alpine AS production
WORKDIR /app
COPY --from=builder /app/dist ./dist
COPY --from=builder /app/node_modules ./node_modules
CMD ["node", "dist/server.js"]
```

#### Advanced Multi-stage với multiple targets

```dockerfile
# Base stage
FROM node:18-alpine AS base
WORKDIR /app
COPY package*.json ./

# Development stage
FROM base AS development
RUN npm install
COPY . .
CMD ["npm", "run", "dev"]

# Build stage
FROM base AS build
RUN npm ci
COPY . .
RUN npm run build

# Test stage
FROM build AS test
RUN npm test

# Production stage
FROM node:18-alpine AS production
WORKDIR /app
COPY --from=build /app/dist ./dist
COPY --from=build /app/node_modules ./node_modules
USER node
CMD ["node", "dist/server.js"]
```

```bash
# Build specific target
docker build --target development -t myapp:dev .
docker build --target production -t myapp:prod .
```

---

### 2. Image Optimization

#### Layer Optimization

```dockerfile
# ❌ Bad - Creates unnecessary layers
RUN apt-get update
RUN apt-get install -y curl
RUN apt-get install -y git
RUN apt-get clean

# ✅ Good - Single layer, clean in same layer
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        curl \
        git && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
```

#### Leverage Build Cache

```dockerfile
# ✅ Copy dependency files first
COPY package*.json ./
RUN npm ci

# Then copy source (changes more frequently)
COPY . .
```

#### Use .dockerignore

```dockerignore
# .dockerignore
node_modules
npm-debug.log
Dockerfile
.dockerignore
.git
.gitignore
README.md
.env
coverage
tests
*.md
```

#### Choose Right Base Image

```dockerfile
# Size comparison:
# node:18          ~900MB
# node:18-slim     ~200MB
# node:18-alpine   ~120MB

# For production, prefer alpine or distroless
FROM node:18-alpine
# or
FROM gcr.io/distroless/nodejs18-debian11
```

---

### 3. BuildKit Features

#### Enable BuildKit

```bash
# Environment variable
export DOCKER_BUILDKIT=1
docker build .

# Or in daemon.json
{
  "features": {
    "buildkit": true
  }
}
```

#### Cache Mounts

```dockerfile
# Cache npm packages
RUN --mount=type=cache,target=/root/.npm \
    npm ci

# Cache apt packages
RUN --mount=type=cache,target=/var/cache/apt \
    apt-get update && apt-get install -y git
```

#### Secret Mounts

```dockerfile
# Mount secrets during build (not stored in image)
RUN --mount=type=secret,id=npmrc,target=/root/.npmrc \
    npm ci
```

```bash
docker build --secret id=npmrc,src=$HOME/.npmrc .
```

#### SSH Mounts

```dockerfile
# Clone private repos
RUN --mount=type=ssh \
    git clone git@github.com:private/repo.git
```

```bash
docker build --ssh default .
```

---

### 4. Security Best Practices

#### Run as Non-root User

```dockerfile
# Create user
RUN addgroup -S appgroup && adduser -S appuser -G appgroup

# Change ownership
COPY --chown=appuser:appgroup . .

# Switch user
USER appuser

CMD ["node", "server.js"]
```

#### Use Read-only Filesystem

```bash
docker run --read-only \
  --tmpfs /tmp \
  --tmpfs /var/run \
  myapp
```

#### Scan for Vulnerabilities

```bash
# Docker Scout (built-in)
docker scout cves myimage:tag

# Trivy
trivy image myimage:tag

# Snyk
snyk container test myimage:tag
```

#### Minimal Base Images

```dockerfile
# Use distroless for minimal attack surface
FROM gcr.io/distroless/static-debian11

# Or scratch for Go binaries
FROM scratch
COPY myapp /myapp
CMD ["/myapp"]
```

#### Don't Store Secrets in Images

```dockerfile
# ❌ Bad
ENV API_KEY=secret123

# ✅ Good - Use runtime injection
# docker run -e API_KEY=secret123 myapp
```

---

### 5. Health Checks

```dockerfile
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
  CMD curl -f http://localhost:3000/health || exit 1

# Or with wget (for alpine)
HEALTHCHECK --interval=30s --timeout=3s \
  CMD wget --quiet --tries=1 --spider http://localhost:3000/health || exit 1
```

---

### 6. Resource Limits

```bash
# Memory limit
docker run -m 512m myapp

# CPU limit
docker run --cpus=".5" myapp

# Combined
docker run -m 512m --cpus="1" myapp
```

```yaml
# docker-compose.yml
services:
  app:
    image: myapp
    deploy:
      resources:
        limits:
          cpus: '0.50'
          memory: 512M
        reservations:
          cpus: '0.25'
          memory: 256M
```

---

### 7. Debugging Containers

```bash
# Execute into running container
docker exec -it container_name sh

# View logs
docker logs -f container_name

# Inspect container
docker inspect container_name

# View processes
docker top container_name

# View resource usage
docker stats container_name

# Copy files from container
docker cp container_name:/path/to/file ./local/path

# View filesystem changes
docker diff container_name
```

#### Debug Crashed Container

```bash
# Run with shell to debug
docker run -it --entrypoint sh myimage

# Start stopped container for debugging
docker commit crashed_container debug_image
docker run -it debug_image sh
```

---

### 8. Docker Internals

#### Namespaces

- **PID**: Process isolation
- **NET**: Network isolation
- **MNT**: Filesystem isolation
- **UTS**: Hostname isolation
- **IPC**: Inter-process communication
- **USER**: User isolation

#### Control Groups (cgroups)

- Resource limiting (CPU, memory)
- Prioritization
- Accounting
- Control

#### Union Filesystem

- Layered filesystem
- Copy-on-write
- Image layers are read-only
- Container layer is writable

---

## 🛠️ Best Practices Summary

| Practice | Description |
|----------|-------------|
| Multi-stage builds | Separate build and runtime |
| Alpine/Distroless | Minimal base images |
| Non-root user | Security |
| .dockerignore | Smaller build context |
| Layer ordering | Better cache utilization |
| Health checks | Container health monitoring |
| Resource limits | Prevent resource exhaustion |
| Image scanning | Security vulnerabilities |

---

## 📖 Resources

- [Docker Best Practices](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
- [BuildKit Documentation](https://docs.docker.com/build/buildkit/)
- [Docker Security](https://docs.docker.com/engine/security/)

---

## 📝 Module Files (Các file trong Module)

| File | Description (Mô tả) |
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

| ← Previous (Trước) | Current (Hiện tại) | Next (Tiếp) → |
|:------------------:|:------------------:|:-------------:|
| [Track 1 Capstone](../../Track1_Foundation_StaticWeb/1.8_Capstone_Project/) | **2.1 Docker Advanced** | [2.2 Docker Compose](../2.2_Docker_Compose/) |

---

**Level up your Docker skills! 🐳**

*Nâng cấp kỹ năng Docker của bạn!*

</div>
