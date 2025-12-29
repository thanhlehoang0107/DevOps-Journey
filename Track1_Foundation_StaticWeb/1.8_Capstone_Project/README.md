# 🏆 Module 1.8: Capstone Project

> **Static Website with Full CI/CD Pipeline** - Integrate all Track 1 knowledge.
>
> *Website tĩnh với Full CI/CD Pipeline - Tích hợp toàn bộ kiến thức Track 1.*

---

## 🎯 Project Overview (Tổng quan dự án)

Build a **static portfolio website** with (Xây dựng portfolio website tĩnh với):

- ✅ Source code managed with Git (Quản lý bằng Git)
- ✅ Static website with HTML/CSS/JS
- ✅ Containerized with Docker + NGINX
- ✅ CI/CD pipeline with GitHub Actions
- ✅ Auto deploy when pushing code (Tự động deploy khi push code)

---

## 📐 Project Requirements

### 1. Functional Requirements

| # | Requirement | Mô tả |
|---|-------------|-------|
| FR-01 | Homepage | Trang giới thiệu bản thân |
| FR-02 | About page | Chi tiết về skills, kinh nghiệm |
| FR-03 | Projects page | Showcase các projects |
| FR-04 | Contact form | Form liên hệ (UI only) |
| FR-05 | Responsive | Hiển thị tốt trên mobile/tablet/desktop |

### 2. Technical Requirements

| # | Requirement | Mô tả |
|---|-------------|-------|
| TR-01 | Git | Quản lý code với Git, có .gitignore |
| TR-02 | Docker | Dockerfile để build image |
| TR-03 | NGINX | Serve static files với NGINX |
| TR-04 | CI | GitHub Actions workflow cho lint/build |
| TR-05 | CD | Auto deploy khi push main branch |
| TR-06 | Docker Hub | Push image lên registry |

---

## 📁 Project Structure

```
devops-portfolio/
│
├── .github/
│   └── workflows/
│       └── deploy.yml              # CI/CD workflow
│
├── src/                            # Source code
│   ├── index.html
│   ├── about.html
│   ├── projects.html
│   ├── contact.html
│   ├── css/
│   │   └── style.css
│   ├── js/
│   │   └── main.js
│   └── images/
│       └── profile.jpg
│
├── nginx/
│   └── nginx.conf                  # NGINX configuration
│
├── Dockerfile                      # Docker build file
├── .dockerignore                   # Docker ignore
├── .gitignore                      # Git ignore
├── README.md                       # Project documentation
└── LICENSE                         # License file
```

---

## 📝 Step-by-Step Guide

### Step 1: Tạo Project 📂

```bash
# 1. Tạo thư mục project
mkdir devops-portfolio
cd devops-portfolio

# 2. Khởi tạo Git
git init

# 3. Tạo cấu trúc thư mục
mkdir -p src/{css,js,images}
mkdir -p nginx
mkdir -p .github/workflows

# 4. Tạo .gitignore
cat > .gitignore << 'EOF'
# OS files
.DS_Store
Thumbs.db

# IDE
.vscode/
.idea/

# Node modules (nếu dùng build tools)
node_modules/

# Logs
*.log

# Environment files
.env
.env.local
EOF
```

---

### Step 2: Tạo Website 🌐

#### index.html

```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DevOps Portfolio</title>
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <header>
        <nav>
            <div class="logo">🚀 DevOps Journey</div>
            <ul class="nav-links">
                <li><a href="index.html" class="active">Home</a></li>
                <li><a href="about.html">About</a></li>
                <li><a href="projects.html">Projects</a></li>
                <li><a href="contact.html">Contact</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <section class="hero">
            <h1>Hi, I'm a DevOps Engineer 👋</h1>
            <p>Building reliable, scalable infrastructure</p>
            <a href="projects.html" class="btn">View My Projects</a>
        </section>

        <section class="skills">
            <h2>Skills</h2>
            <div class="skill-cards">
                <div class="card">
                    <span class="icon">🐧</span>
                    <h3>Linux</h3>
                </div>
                <div class="card">
                    <span class="icon">🐳</span>
                    <h3>Docker</h3>
                </div>
                <div class="card">
                    <span class="icon">⚙️</span>
                    <h3>CI/CD</h3>
                </div>
                <div class="card">
                    <span class="icon">☸️</span>
                    <h3>Kubernetes</h3>
                </div>
            </div>
        </section>
    </main>

    <footer>
        <p>© 2025 DevOps Journey. Built with 💙</p>
    </footer>

    <script src="js/main.js"></script>
</body>
</html>
```

#### css/style.css

```css
/* Reset */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    line-height: 1.6;
    color: #333;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    min-height: 100vh;
}

/* Header */
header {
    background: rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(10px);
    padding: 1rem 2rem;
    position: sticky;
    top: 0;
    z-index: 100;
}

nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    max-width: 1200px;
    margin: 0 auto;
}

.logo {
    font-size: 1.5rem;
    font-weight: bold;
    color: white;
}

.nav-links {
    display: flex;
    list-style: none;
    gap: 2rem;
}

.nav-links a {
    color: white;
    text-decoration: none;
    padding: 0.5rem 1rem;
    border-radius: 5px;
    transition: background 0.3s;
}

.nav-links a:hover,
.nav-links a.active {
    background: rgba(255, 255, 255, 0.2);
}

/* Hero */
.hero {
    text-align: center;
    padding: 100px 20px;
    color: white;
}

.hero h1 {
    font-size: 3rem;
    margin-bottom: 1rem;
}

.hero p {
    font-size: 1.5rem;
    margin-bottom: 2rem;
    opacity: 0.9;
}

.btn {
    display: inline-block;
    padding: 1rem 2rem;
    background: white;
    color: #667eea;
    text-decoration: none;
    border-radius: 50px;
    font-weight: bold;
    transition: transform 0.3s, box-shadow 0.3s;
}

.btn:hover {
    transform: translateY(-3px);
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
}

/* Skills */
.skills {
    background: white;
    padding: 80px 20px;
    text-align: center;
}

.skills h2 {
    font-size: 2.5rem;
    margin-bottom: 3rem;
    color: #333;
}

.skill-cards {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 2rem;
    max-width: 1000px;
    margin: 0 auto;
}

.card {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    padding: 2rem;
    border-radius: 15px;
    color: white;
    transition: transform 0.3s;
}

.card:hover {
    transform: translateY(-10px);
}

.card .icon {
    font-size: 3rem;
    display: block;
    margin-bottom: 1rem;
}

.card h3 {
    font-size: 1.3rem;
}

/* Footer */
footer {
    text-align: center;
    padding: 2rem;
    color: white;
    background: rgba(0, 0, 0, 0.1);
}

/* Responsive */
@media (max-width: 768px) {
    .nav-links {
        display: none;
    }
    
    .hero h1 {
        font-size: 2rem;
    }
    
    .hero p {
        font-size: 1.2rem;
    }
}
```

#### js/main.js

```javascript
// Simple interactivity
document.addEventListener('DOMContentLoaded', function() {
    console.log('🚀 DevOps Portfolio loaded!');
    
    // Add animation on scroll
    const cards = document.querySelectorAll('.card');
    cards.forEach((card, index) => {
        card.style.animationDelay = `${index * 0.1}s`;
    });
});
```

---

### Step 3: Tạo Docker Configuration 🐳

#### Dockerfile

```dockerfile
# Build stage (optional, for future use with build tools)
FROM nginx:alpine

# Labels
LABEL maintainer="yourname@example.com"
LABEL version="1.0"
LABEL description="DevOps Portfolio Website"

# Copy NGINX config
COPY nginx/nginx.conf /etc/nginx/conf.d/default.conf

# Copy website files
COPY src/ /usr/share/nginx/html/

# Expose port
EXPOSE 80

# Health check
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
    CMD wget --no-verbose --tries=1 --spider http://localhost/ || exit 1

# Start NGINX
CMD ["nginx", "-g", "daemon off;"]
```

#### nginx/nginx.conf

```nginx
server {
    listen 80;
    server_name localhost;
    root /usr/share/nginx/html;
    index index.html;

    # Security headers
    add_header X-Frame-Options "SAMEORIGIN" always;
    add_header X-Content-Type-Options "nosniff" always;
    add_header X-XSS-Protection "1; mode=block" always;

    # Gzip compression
    gzip on;
    gzip_vary on;
    gzip_min_length 1024;
    gzip_types text/plain text/css text/javascript application/javascript application/json;

    # Serve static files
    location / {
        try_files $uri $uri/ /index.html;
    }

    # Cache static assets
    location ~* \.(css|js|jpg|jpeg|png|gif|ico|svg|woff|woff2)$ {
        expires 1y;
        add_header Cache-Control "public, immutable";
    }

    # Custom error pages
    error_page 404 /404.html;
    error_page 500 502 503 504 /50x.html;
}
```

#### .dockerignore

```
.git
.github
.gitignore
README.md
LICENSE
*.md
.DS_Store
Thumbs.db
```

---

### Step 4: Test Local 🧪

```bash
# Build Docker image
docker build -t devops-portfolio:dev .

# Run container
docker run -d -p 8080:80 --name portfolio devops-portfolio:dev

# Test
curl http://localhost:8080
# Mở browser: http://localhost:8080

# View logs
docker logs portfolio

# Stop and clean up
docker stop portfolio
docker rm portfolio
```

---

### Step 5: CI/CD Pipeline ⚙️

#### .github/workflows/deploy.yml

```yaml
name: Build and Deploy

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

env:
  REGISTRY: ghcr.io
  IMAGE_NAME: ${{ github.repository }}

jobs:
  # Job 1: Lint and Test
  lint:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Check HTML files exist
        run: |
          echo "Checking required files..."
          test -f src/index.html && echo "✅ index.html exists"
          test -f src/css/style.css && echo "✅ style.css exists"
          test -f Dockerfile && echo "✅ Dockerfile exists"

      - name: Validate Dockerfile
        uses: hadolint/hadolint-action@v3.1.0
        with:
          dockerfile: Dockerfile
          failure-threshold: warning

  # Job 2: Build Docker Image
  build:
    runs-on: ubuntu-latest
    needs: lint
    permissions:
      contents: read
      packages: write
    
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v3

      - name: Log in to Container Registry
        if: github.event_name != 'pull_request'
        uses: docker/login-action@v3
        with:
          registry: ${{ env.REGISTRY }}
          username: ${{ github.actor }}
          password: ${{ secrets.GITHUB_TOKEN }}

      - name: Extract metadata
        id: meta
        uses: docker/metadata-action@v5
        with:
          images: ${{ env.REGISTRY }}/${{ env.IMAGE_NAME }}
          tags: |
            type=ref,event=branch
            type=sha,prefix=
            type=raw,value=latest,enable={{is_default_branch}}

      - name: Build and push
        uses: docker/build-push-action@v5
        with:
          context: .
          push: ${{ github.event_name != 'pull_request' }}
          tags: ${{ steps.meta.outputs.tags }}
          labels: ${{ steps.meta.outputs.labels }}
          cache-from: type=gha
          cache-to: type=gha,mode=max

  # Job 3: Deploy (Optional - GitHub Pages)
  deploy-pages:
    runs-on: ubuntu-latest
    needs: build
    if: github.ref == 'refs/heads/main' && github.event_name == 'push'
    
    permissions:
      contents: read
      pages: write
      id-token: write
    
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Pages
        uses: actions/configure-pages@v4

      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: './src'

      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

---

### Step 6: Push to GitHub 🚀

```bash
# Thêm remote
git remote add origin https://github.com/YOUR_USERNAME/devops-portfolio.git

# Commit tất cả
git add .
git commit -m "Initial commit: DevOps Portfolio with CI/CD"

# Push
git push -u origin main
```

---

## ✅ Tiêu chí đánh giá

| # | Tiêu chí | Điểm | Mô tả |
|---|----------|------|-------|
| 1 | **Website** | 20% | HTML/CSS đúng chuẩn, responsive |
| 2 | **Git** | 10% | Commit messages rõ ràng, .gitignore |
| 3 | **Dockerfile** | 20% | Build thành công, tối ưu layers |
| 4 | **NGINX** | 15% | Config đúng, security headers |
| 5 | **CI/CD** | 25% | Pipeline chạy thành công |
| 6 | **README** | 10% | Documentation đầy đủ |

---

## 🎯 Bonus Challenges

Sau khi hoàn thành yêu cầu cơ bản, thử các challenges sau:

### Challenge 1: Multi-stage Build ⭐

Thêm build step cho CSS/JS minification

### Challenge 2: Custom Domain ⭐⭐

Cấu hình custom domain cho GitHub Pages

### Challenge 3: SSL/HTTPS ⭐⭐

Cấu hình HTTPS với Let's Encrypt

### Challenge 4: Monitoring ⭐⭐⭐

Thêm uptime monitoring với UptimeRobot

---

## 📚 Resources

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Docker Best Practices](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
- [NGINX Documentation](https://nginx.org/en/docs/)
- [GitHub Pages](https://pages.github.com/)

---

<div align="center">

### 🔗 Module Navigation (Điều hướng Module)

| ← Previous | Current | Next → |
|:------------------:|:------------------:|:-------------:|
| [1.7 CI/CD](../1.7_CICD_Basic/) | **1.8 Capstone** | [Track 2](../../Track2_Orchestration_Automation/) |

---

**🎉 Congratulations! You completed Track 1!**

*Chúc mừng! Bạn đã hoàn thành Track 1!*

</div>
