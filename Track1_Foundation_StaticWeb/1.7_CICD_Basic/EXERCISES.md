# 💪 Exercises: CI/CD Basic

> Bài tập tự luyện GitHub Actions.

---

## Exercise 1: Basic Workflow ⭐

Tạo workflow:

1. Trigger on push to main
2. Run on ubuntu-latest
3. Checkout code
4. Print "Hello CI/CD"
5. Show git commit info

---

## Exercise 2: Node.js CI ⭐⭐

Tạo CI workflow cho Node.js app:

1. Install dependencies
2. Run linting
3. Run tests
4. Upload coverage report as artifact

---

## Exercise 3: Docker Build ⭐⭐

Tạo workflow:

1. Build Docker image
2. Tag với commit SHA
3. Push to Docker Hub
4. (Optional) Push to GitHub Container Registry

---

## Exercise 4: Matrix Testing ⭐⭐

Test trên multiple environments:

- OS: ubuntu, windows
- Node versions: 16, 18, 20
- Report failures

---

## Exercise 5: Deployment Pipeline ⭐⭐⭐

Tạo complete pipeline:

1. Build stage
2. Test stage
3. Deploy to staging (manual approval)
4. Deploy to production (on main only)

---

## Exercise 6: Reusable Workflow ⭐⭐⭐

Tạo reusable workflow:

1. Create callable workflow
2. Accept inputs (node-version, environment)
3. Use from another workflow
4. Pass secrets properly

---

## Exercise 7: Scheduled Jobs ⭐⭐

Tạo scheduled workflow:

1. Run daily at midnight
2. Check dependencies for vulnerabilities
3. Send notification if issues found

---

## 📝 Checklist

- [ ] Exercise 1: Basic Workflow
- [ ] Exercise 2: Node.js CI
- [ ] Exercise 3: Docker Build
- [ ] Exercise 4: Matrix Testing
- [ ] Exercise 5: Deployment Pipeline
- [ ] Exercise 6: Reusable Workflow
- [ ] Exercise 7: Scheduled Jobs

---

**[← Back to README](./README.md)** | **[View Solutions →](./SOLUTIONS.md)**
