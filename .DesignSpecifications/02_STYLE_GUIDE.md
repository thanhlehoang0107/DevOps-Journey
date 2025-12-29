# 🎨 STYLE GUIDE - Quy Ước Viết Code & Config

---

## 📋 DOCUMENT INFORMATION (Thông tin tài liệu)

| Thuộc tính | Giá trị |
|------------|---------|
| **Tên** | Style Guide |
| **Phiên bản** | 1.0 |
| **Ngày tạo** | 2025-12-28 |
| **Mô tả** | Quy ước viết code samples, config, commands trong tài liệu |

---

## 1. 🎯 PURPOSE (Mục đích)

Đảm bảo **tính nhất quán** khi viết:

- Code samples (Bash, Python, etc.)
- Configuration files (YAML, JSON, Dockerfile, etc.)
- Commands và Output

---

## 2. 💻 BASH / SHELL

### 2.1 Cấu trúc lệnh

```bash
# ✅ ĐÚNG: Có comment giải thích
# Tạo thư mục project
mkdir -p project-name/src

# ❌ SAI: Không có comment
mkdir -p project-name/src
```

### 2.2 Quy ước

| Quy tắc | Ví dụ |
|---------|-------|
| Comment trước mỗi lệnh | `# Mô tả lệnh` |
| Dùng `--long-flag` thay vì `-l` | `docker run --detach` thay vì `docker run -d` |
| Placeholder dùng `<...>` | `docker exec -it <container_name> bash` |
| Biến môi trường dùng `${VAR}` | `echo ${HOME}` |

### 2.3 Template

```bash
# =============================================
# Mô tả ngắn: Mục đích của script/lệnh
# =============================================

# Bước 1: Mô tả
command --option value

# Bước 2: Mô tả  
another-command \
  --multi-line \
  --option

# Verify
verify-command
```

---

## 3. 📄 YAML

### 3.1 Cấu trúc

```yaml
# ✅ ĐÚNG: Có comment, indent 2 spaces
# docker-compose.yml
version: "3.8"

services:
  # Web service
  web:
    image: nginx:alpine
    ports:
      - "80:80"
    # Volumes for static files
    volumes:
      - ./html:/usr/share/nginx/html:ro
```

### 3.2 Quy ước

| Quy tắc | Mô tả |
|---------|-------|
| Indent | 2 spaces (không dùng tab) |
| Quotes | Dùng `"` cho strings có special chars |
| Comment | `#` ở đầu dòng hoặc cuối dòng |
| Tên file | Ghi ở comment đầu tiên |

---

## 4. 🐳 DOCKERFILE

### 4.1 Cấu trúc

```dockerfile
# =============================================
# Stage 1: Build
# =============================================
FROM node:18-alpine AS builder

# Set working directory
WORKDIR /app

# Copy package files first (cache optimization)
COPY package*.json ./

# Install dependencies
RUN npm ci --only=production

# Copy source code
COPY . .

# Build application
RUN npm run build

# =============================================
# Stage 2: Production
# =============================================
FROM node:18-alpine

WORKDIR /app

# Copy from builder
COPY --from=builder /app/dist ./dist
COPY --from=builder /app/node_modules ./node_modules

# Run as non-root user
USER node

# Expose port
EXPOSE 3000

# Start application
CMD ["node", "dist/index.js"]
```

### 4.2 Quy ước

| Quy tắc | Mô tả |
|---------|-------|
| Base image | Luôn có tag cụ thể (`node:18-alpine` không phải `node:latest`) |
| Multi-stage | Ưu tiên sử dụng |
| COPY trước RUN | Tối ưu cache |
| USER | Không chạy root trong production |
| Comment | Phân chia stages rõ ràng |

---

## 5. 📋 KUBERNETES YAML

### 5.1 Cấu trúc

```yaml
# deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
  labels:
    app: my-app
    version: v1
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
        - name: my-app
          image: my-app:1.0.0
          ports:
            - containerPort: 8080
          # Resources limits
          resources:
            requests:
              memory: "128Mi"
              cpu: "100m"
            limits:
              memory: "256Mi"
              cpu: "200m"
```

### 5.2 Quy ước

| Quy tắc | Mô tả |
|---------|-------|
| Tên file | Ghi ở comment đầu tiên |
| Labels | Luôn có `app` và `version` |
| Resources | Luôn set requests và limits |
| Image tag | Cụ thể version, không dùng `latest` |

---

## 6. 🔧 TERRAFORM HCL

### 6.1 Cấu trúc

```hcl
# main.tf
# =============================================
# AWS EC2 Instance
# =============================================

resource "aws_instance" "web" {
  # Use latest Amazon Linux 2 AMI
  ami           = data.aws_ami.amazon_linux.id
  instance_type = var.instance_type

  # Network configuration
  subnet_id              = var.subnet_id
  vpc_security_group_ids = [aws_security_group.web.id]

  # Tags
  tags = {
    Name        = "${var.project}-web"
    Environment = var.environment
    ManagedBy   = "Terraform"
  }
}
```

### 6.2 Quy ước

| Quy tắc | Mô tả |
|---------|-------|
| Tên file | `main.tf`, `variables.tf`, `outputs.tf` |
| Indent | 2 spaces |
| Tags | Luôn có `Name`, `Environment`, `ManagedBy` |
| Variables | Prefix với `var.` |

---

## 7. 📟 OUTPUT / EXPECTED OUTPUT

### 7.1 Cấu trúc

```bash
# Lệnh
docker ps

# Output
CONTAINER ID   IMAGE          STATUS          PORTS                  NAMES
abc123def456   nginx:alpine   Up 2 minutes    0.0.0.0:80->80/tcp     web
```

### 7.2 Quy ước

| Quy tắc | Mô tả |
|---------|-------|
| Tách lệnh và output | Dùng comment `# Output` |
| Truncate | Dùng `...` nếu output quá dài |
| Highlight | **Bold** phần quan trọng trong text |

---

## 8. ✅ CHECKLIST (Danh sách kiểm tra)

Khi viết code samples:

- [ ] Có comment giải thích
- [ ] Dùng placeholder `<...>` cho giá trị thay đổi
- [ ] Có language tag cho code block
- [ ] Output mẫu nếu cần verify
- [ ] Indent đúng quy cách (2 spaces)
- [ ] Không dùng `latest` tag

---

## 9. 📚 REFERENCES (Tham khảo)

- [Google Shell Style Guide](https://google.github.io/styleguide/shellguide.html)
- [Dockerfile Best Practices](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
- [Kubernetes YAML Best Practices](https://kubernetes.io/docs/concepts/configuration/overview/)

---

*Cập nhật: 2025-12-28 | Phiên bản: 1.0*

