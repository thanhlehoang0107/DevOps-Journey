# 🔬 Labs: CI/CD Basic

> Bài thực hành GitHub Actions.

---

## 🔬 Lab 1: First Workflow

```yaml
# .github/workflows/hello.yml
name: Hello World

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  hello:
    runs-on: ubuntu-latest
    
    steps:
      - name: Say Hello
        run: echo "Hello, GitHub Actions!"
      
      - name: Show date
        run: date
      
      - name: Show environment
        run: |
          echo "Runner OS: $RUNNER_OS"
          echo "GitHub Actor: $GITHUB_ACTOR"
```

---

## 🔬 Lab 2: Checkout and Build

```yaml
name: Build

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest
    
    steps:
      - uses: actions/checkout@v4
      
      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '18'
      
      - name: Install dependencies
        run: npm install
      
      - name: Run build
        run: npm run build
```

---

## 🔬 Lab 3: Testing

```yaml
name: Test

on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    
    steps:
      - uses: actions/checkout@v4
      
      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '18'
          cache: 'npm'
      
      - run: npm ci
      - run: npm test
      
      - name: Upload test results
        uses: actions/upload-artifact@v4
        with:
          name: test-results
          path: coverage/
```

---

## 🔬 Lab 4: Docker Build & Push

```yaml
name: Docker

on:
  push:
    branches: [main]

jobs:
  docker:
    runs-on: ubuntu-latest
    
    steps:
      - uses: actions/checkout@v4
      
      - name: Login to Docker Hub
        uses: docker/login-action@v3
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_TOKEN }}
      
      - name: Build and push
        uses: docker/build-push-action@v5
        with:
          push: true
          tags: user/app:latest
```

---

## 🔬 Lab 5: Matrix Strategy

```yaml
name: Matrix Test

on: [push]

jobs:
  test:
    runs-on: ${{ matrix.os }}
    
    strategy:
      matrix:
        os: [ubuntu-latest, windows-latest]
        node-version: [16, 18, 20]
    
    steps:
      - uses: actions/checkout@v4
      
      - name: Use Node.js ${{ matrix.node-version }}
        uses: actions/setup-node@v4
        with:
          node-version: ${{ matrix.node-version }}
      
      - run: npm test
```

---

## 🔬 Lab 6: Deployment

```yaml
name: Deploy

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    environment: production
    
    steps:
      - uses: actions/checkout@v4
      
      - name: Build
        run: npm run build
      
      - name: Deploy to server
        env:
          SSH_KEY: ${{ secrets.SSH_PRIVATE_KEY }}
        run: |
          echo "$SSH_KEY" > key.pem
          chmod 600 key.pem
          scp -i key.pem -r dist/* user@server:/var/www/app/
```

---

## ✅ Checklist

- [ ] Lab 1: First Workflow
- [ ] Lab 2: Build
- [ ] Lab 3: Testing
- [ ] Lab 4: Docker
- [ ] Lab 5: Matrix
- [ ] Lab 6: Deployment

---

**[← Back to README](./README.md)**
