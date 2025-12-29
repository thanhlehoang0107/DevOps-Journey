# 🔧 Module 2.3: Jenkins

[![Duration](https://img.shields.io/badge/Duration-1%20week-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Intermediate-orange?style=flat-square)](.)

> **CI/CD with Jenkins** - Build automation server.
>
> *CI/CD với Jenkins - Máy chủ tự động hóa build.*

---

## 🎯 Learning Objectives (Mục tiêu học tập)

After this module, you will (Sau module này, bạn sẽ):

- ✅ Install and configure Jenkins (Cài đặt và cấu hình Jenkins)
- ✅ Create Jenkins pipelines (Tạo pipeline Jenkins)
- ✅ Master Jenkinsfile syntax (Thành thạo cú pháp Jenkinsfile)
- ✅ Implement Pipeline as Code (Triển khai Pipeline dạng code)
- ✅ Integrate with Docker and Git (Tích hợp với Docker và Git)
- ✅ Use Blue Ocean interface (Sử dụng giao diện Blue Ocean)

---

## 📚 Content (Nội dung)

### 1. Jenkins Installation (Cài đặt Jenkins)

```bash
# Docker
docker run -d -p 8080:8080 -p 50000:50000 \
  -v jenkins_home:/var/jenkins_home \
  --name jenkins \
  jenkins/jenkins:lts
```

### 2. Pipeline Basics (Pipeline cơ bản)

```groovy
// Jenkinsfile
pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }
        
        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
        
        stage('Deploy') {
            steps {
                sh 'docker build -t myapp .'
                sh 'docker push myapp'
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
```

### 3. Declarative vs Scripted

```groovy
// Declarative (Khai báo)
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
    }
}

// Scripted (Script)
node {
    stage('Build') {
        echo 'Building...'
    }
}
```

### 4. Docker Integration (Tích hợp Docker)

```groovy
pipeline {
    agent {
        docker {
            image 'node:18'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
    }
}
```

---

## 📝 Module Files (Các file trong Module)

| File | Description (Mô tả) |
|------|---------------------|
| [LABS.md](./LABS.md) | Hands-on labs (Bài thực hành) |
| [QUIZ.md](./QUIZ.md) | Knowledge check (Kiểm tra kiến thức) |
| [EXERCISES.md](./EXERCISES.md) | Exercises (Bài tập) |
| [PROJECT.md](./PROJECT.md) | Mini project (Dự án nhỏ) |
| [SOLUTIONS.md](./SOLUTIONS.md) | Solutions (Đáp án) |
| [CHEATSHEET.md](./CHEATSHEET.md) | Quick reference (Tra cứu nhanh) |

---

<div align="center">

### 🔗 Module Navigation (Điều hướng Module)

| ← Previous (Trước) | Current (Hiện tại) | Next (Tiếp) → |
|:------------------:|:------------------:|:-------------:|
| [2.2 Docker Compose](../2.2_Docker_Compose/) | **2.3 Jenkins** | [2.4 Kubernetes](../2.4_Kubernetes_Core/) |

---

**Automate your CI/CD! 🔧**

*Tự động hóa CI/CD của bạn!*

</div>
