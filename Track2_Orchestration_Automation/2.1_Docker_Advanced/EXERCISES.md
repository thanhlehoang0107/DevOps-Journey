# 💪 Exercises: Docker Advanced

> Bài tập tự luyện Docker nâng cao.

---

## Exercise 1: Multi-stage Optimization ⭐⭐

Có Dockerfile sau:

```dockerfile
FROM node:18
WORKDIR /app
COPY . .
RUN npm install
CMD ["node", "server.js"]
```

**Task**: Viết lại với:

1. Multi-stage build
2. Alpine base
3. Non-root user
4. Health check
5. Target size < 150MB

---

## Exercise 2: BuildKit Advanced ⭐⭐

Tạo Dockerfile sử dụng:

1. Cache mount cho npm
2. Secret mount cho private npm registry
3. Build args cho version
4. Multiple build targets (dev, test, prod)

---

## Exercise 3: Security Audit ⭐⭐⭐

Cho image sau, tìm và fix security issues:

```dockerfile
FROM ubuntu:latest
RUN apt-get update && apt-get install -y nodejs npm
COPY . /app
WORKDIR /app
ENV API_KEY=supersecret123
RUN npm install
EXPOSE 3000
CMD ["npm", "start"]
```

---

## Exercise 4: Image Size Challenge ⭐⭐⭐

Có Go application:

```go
package main
import "fmt"
func main() {
    fmt.Println("Hello DevOps!")
}
```

**Task**: Tạo Docker image với size < 10MB

---

## Exercise 5: Layer Analysis ⭐⭐

Phân tích image layers:

1. Sử dụng `docker history`
2. Cài đặt và sử dụng `dive`
3. Identify wasted space
4. Optimize và compare

---

## Exercise 6: Resource Management ⭐⭐⭐

Viết docker-compose.yml với:

1. Memory limits cho mỗi service
2. CPU limits
3. Restart policies
4. Health checks
5. Logging configuration

---

## 📝 Checklist

- [ ] Exercise 1: Multi-stage Optimization
- [ ] Exercise 2: BuildKit Advanced
- [ ] Exercise 3: Security Audit
- [ ] Exercise 4: Image Size Challenge
- [ ] Exercise 5: Layer Analysis
- [ ] Exercise 6: Resource Management

---

**[← Back to README](./README.md)** | **[View Solutions →](./SOLUTIONS.md)**
