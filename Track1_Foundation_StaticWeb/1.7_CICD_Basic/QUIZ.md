# ❓ Quiz: CI/CD Basic

> 15 câu hỏi về CI/CD và GitHub Actions.

---

### Q1

CI là viết tắt của?

a) Container Integration  
b) Continuous Integration  
c) Code Integration  
d) Complete Integration  

---

### Q2

CD có thể là?

a) Continuous Delivery  
b) Continuous Deployment  
c) Cả a và b  
d) Continuous Development  

---

### Q3

GitHub Actions workflow files ở đâu?

a) .github/actions/  
b) .github/workflows/  
c) .workflows/  
d) workflows/  

---

### Q4

`on: push` có nghĩa gì?

a) Trigger manually  
b) Trigger on push event  
c) Trigger on schedule  
d) Trigger on PR  

---

### Q5

`runs-on: ubuntu-latest` là gì?

a) Docker image  
b) Runner OS  
c) Node version  
d) Branch name  

---

### Q6

Actions `actions/checkout@v4` làm gì?

a) Create checkout  
b) Clone repository  
c) Push code  
d) Delete code  

---

### Q7

Secrets được access bằng?

a) `$SECRETS.NAME`  
b) `${{ secrets.NAME }}`  
c) `secrets.NAME`  
d) `$secrets.NAME`  

---

### Q8

Matrix strategy dùng để?

a) Run jobs in sequence  
b) Run same job with different configs  
c) Matrix multiplication  
d) Define variables  

---

### Q9

`needs: build` trong job có nghĩa gì?

a) Need build tool  
b) Wait for build job  
c) Skip build  
d) Run before build  

---

### Q10

Environment variables được set bằng?

a) `vars:`  
b) `env:`  
c) `environment:`  
d) `variables:`  

---

### Q11

Artifacts dùng để?

a) Create containers  
b) Share data between jobs  
c) Define secrets  
d) Run tests  

---

### Q12

`if: github.ref == 'refs/heads/main'` có nghĩa gì?

a) Always run  
b) Run only on main branch  
c) Skip main branch  
d) Run on PR  

---

### Q13

Caching trong Actions giúp gì?

a) Speed up workflows  
b) Store secrets  
c) Run parallel  
d) Deploy faster  

---

### Q14

`continue-on-error: true` làm gì?

a) Stop on error  
b) Continue if step fails  
c) Retry on error  
d) Log errors only  

---

### Q15

Workflow dispatch là gì?

a) Auto trigger  
b) Manual trigger  
c) Scheduled trigger  
d) PR trigger  

---

## 📝 Answers

<details>
<summary>Click để xem đáp án</summary>

| Q | A | Q | A |
|---|---|---|---|
| 1 | b | 9 | b |
| 2 | c | 10 | b |
| 3 | b | 11 | b |
| 4 | b | 12 | b |
| 5 | b | 13 | a |
| 6 | b | 14 | b |
| 7 | b | 15 | b |
| 8 | b |   |   |

</details>

---

**[← Back to README](./README.md)**
