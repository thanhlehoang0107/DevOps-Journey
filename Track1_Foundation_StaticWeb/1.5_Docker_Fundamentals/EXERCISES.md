# 💪 Exercises: Docker Fundamentals

> Bài tập tự luyện Docker.

---

## Exercise 1: Container Basics ⭐

1. Run nginx container với custom name
2. Exec vào container và check nginx version
3. Copy file từ container ra host
4. View container logs
5. Stop, start, restart container
6. Remove container

---

## Exercise 2: Dockerfile ⭐⭐

Viết Dockerfile cho Node.js app:

Requirements:

- Base image: node:18-alpine
- Working directory: /app
- Copy package.json first (for caching)
- Install dependencies
- Copy source code
- Expose port 3000
- Run với non-root user

---

## Exercise 3: Multi-stage Build ⭐⭐

Viết multi-stage Dockerfile cho React app:

Stage 1: Build

- Use node:18 as builder
- Install dependencies
- Build production bundle

Stage 2: Serve

- Use nginx:alpine
- Copy build output
- Configure nginx

Target: Final image < 50MB

---

## Exercise 4: Volumes ⭐⭐

1. Create named volume `mydata`
2. Run MySQL container với volume cho /var/lib/mysql
3. Insert some data
4. Stop và remove container
5. Run new container với same volume
6. Verify data persisted

---

## Exercise 5: Networking ⭐⭐⭐

1. Create custom bridge network
2. Run frontend container
3. Run backend API container
4. Run database container
5. Verify containers can communicate by name
6. Inspect network

---

## Exercise 6: Docker Compose (Preview) ⭐⭐⭐

Viết docker-compose.yml cho:

- Frontend (nginx)
- Backend (node)
- Database (postgres)
- Với networks và volumes

---

## Exercise 7: Image Optimization ⭐⭐⭐

Optimize Dockerfile:

- Reduce image size
- Minimize layers
- Use .dockerignore
- Non-root user
- Health check

Compare before/after image sizes.

---

## 📝 Checklist

- [ ] Exercise 1: Container Basics
- [ ] Exercise 2: Dockerfile
- [ ] Exercise 3: Multi-stage Build
- [ ] Exercise 4: Volumes
- [ ] Exercise 5: Networking
- [ ] Exercise 6: Docker Compose
- [ ] Exercise 7: Optimization

---

**[← Back to README](./README.md)** | **[View Solutions →](./SOLUTIONS.md)**
