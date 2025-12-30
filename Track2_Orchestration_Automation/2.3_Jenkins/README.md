# 🔧 Module 2.3: Jenkins

[![Duration](https://img.shields.io/badge/Duration-1--2%20weeks-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Intermediate-orange?style=flat-square)](.)

> **CI/CD with Jenkins** - Enterprise-grade automation server.
>
> *CI/CD với Jenkins - Máy chủ tự động hóa cấp doanh nghiệp.*

---

## 💡 Note on CI/CD Tools (Ghi chú về công cụ CI/CD)

> This course uses **GitLab CI** as the primary CI/CD platform (see Module 1.7).
> Jenkins is taught as an **enterprise alternative** commonly used in industry.
>
> *Khóa học này sử dụng **GitLab CI** làm nền tảng CI/CD chính (xem Module 1.7).*
> *Jenkins được dạy như một **lựa chọn enterprise** phổ biến trong ngành.*

| Tool | Best For |
|------|----------|
| **GitLab CI** | GitLab-hosted projects, all-in-one platform |
| **Jenkins** | Enterprise, self-hosted, legacy systems |
| **GitHub Actions** | GitHub-hosted projects |

---

## 🎯 Learning Objectives (Mục tiêu học tập)

After this module, you will (Sau module này, bạn sẽ):

- ✅ Install and configure Jenkins (Cài đặt và cấu hình Jenkins)
- ✅ Create Jenkins pipelines (Tạo pipeline Jenkins)
- ✅ Master Jenkinsfile syntax (Thành thạo cú pháp Jenkinsfile)
- ✅ Implement Pipeline as Code (Triển khai Pipeline dạng code)
- ✅ Integrate with Docker and Git (Tích hợp với Docker và Git)
- ✅ Use Blue Ocean interface (Sử dụng giao diện Blue Ocean)
- ✅ Configure agents and shared libraries (Cấu hình agents và shared libraries)

---

## 📋 Prerequisites (Điều kiện tiên quyết)

- Complete Module 2.1, 2.2 (Hoàn thành Module 2.1, 2.2)
- Docker experience (Kinh nghiệm Docker)
- Familiar with CI/CD concepts from Module 1.7 (Quen với CI/CD từ Module 1.7)

---

## 📚 Content (Nội dung)

### 1. Jenkins Installation (Cài đặt Jenkins)

```bash
# Docker (Recommended - Khuyến nghị)
docker run -d -p 8080:8080 -p 50000:50000 \
  -v jenkins_home:/var/jenkins_home \
  --name jenkins \
  jenkins/jenkins:lts

# Get initial admin password (Lấy mật khẩu admin)
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```

**Post-Installation (Sau khi cài đặt):**

1. Access <http://localhost:8080>
2. Enter initial password
3. Install suggested plugins
4. Create admin user

---

### 2. Pipeline Basics (Pipeline cơ bản)

#### Declarative Pipeline (Khai báo)

```groovy
// Jenkinsfile
pipeline {
    agent any
    
    environment {
        APP_NAME = 'myapp'
        REGISTRY = 'registry.gitlab.com'
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
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
        
        stage('Docker Build') {
            steps {
                sh 'docker build -t ${REGISTRY}/${APP_NAME}:${BUILD_NUMBER} .'
            }
        }
        
        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                sh 'docker push ${REGISTRY}/${APP_NAME}:${BUILD_NUMBER}'
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline succeeded!'
            // slackSend channel: '#devops', message: 'Build Success!'
        }
        failure {
            echo 'Pipeline failed!'
        }
        always {
            cleanWs()
        }
    }
}
```

---

### 3. Declarative vs Scripted (Khai báo vs Script)

```groovy
// Declarative Pipeline (Recommended - Khuyến nghị)
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

// Scripted Pipeline (More flexible - Linh hoạt hơn)
node {
    stage('Build') {
        echo 'Building...'
    }
}
```

---

### 4. Docker Integration (Tích hợp Docker)

```groovy
pipeline {
    agent {
        docker {
            image 'node:18'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }
    
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }
    }
}
```

#### Multiple Docker Agents

```groovy
pipeline {
    agent none
    
    stages {
        stage('Build') {
            agent {
                docker { image 'node:18' }
            }
            steps {
                sh 'npm run build'
            }
        }
        
        stage('Deploy') {
            agent {
                docker { image 'docker:latest' }
            }
            steps {
                sh 'docker build -t myapp .'
            }
        }
    }
}
```

---

### 5. Parallel Stages (Chạy song song)

```groovy
pipeline {
    agent any
    
    stages {
        stage('Test') {
            parallel {
                stage('Unit Tests') {
                    steps {
                        sh 'npm run test:unit'
                    }
                }
                stage('Integration Tests') {
                    steps {
                        sh 'npm run test:integration'
                    }
                }
                stage('Lint') {
                    steps {
                        sh 'npm run lint'
                    }
                }
            }
        }
    }
}
```

---

### 6. Credentials Management (Quản lý credentials)

```groovy
pipeline {
    agent any
    
    environment {
        DOCKER_CREDS = credentials('docker-registry-creds')
        GIT_TOKEN = credentials('gitlab-token')
    }
    
    stages {
        stage('Deploy') {
            steps {
                sh '''
                    echo $DOCKER_CREDS_PSW | docker login -u $DOCKER_CREDS_USR --password-stdin
                    docker push myapp:latest
                '''
            }
        }
    }
}
```

---

### 7. Shared Libraries (Thư viện chia sẻ)

```groovy
// vars/standardPipeline.groovy
def call(Map config) {
    pipeline {
        agent any
        stages {
            stage('Build') {
                steps {
                    sh config.buildCommand ?: 'npm run build'
                }
            }
            stage('Deploy') {
                when {
                    branch 'main'
                }
                steps {
                    sh config.deployCommand ?: 'docker push'
                }
            }
        }
    }
}

// Jenkinsfile - Usage (Sử dụng)
@Library('my-shared-library') _

standardPipeline(
    buildCommand: 'npm run build',
    deployCommand: 'kubectl apply -f k8s/'
)
```

---

## 🔄 Jenkins vs GitLab CI Comparison (So sánh)

| Feature | Jenkins | GitLab CI |
|---------|---------|-----------|
| **Config Language** | Groovy (Jenkinsfile) | YAML (.gitlab-ci.yml) |
| **Setup** | Self-hosted | Built-in with GitLab |
| **Plugins** | 1800+ plugins | Limited but integrated |
| **Learning Curve** | Steeper | Easier |
| **Best For** | Enterprise, legacy | GitLab projects |

---

## 📝 Module Files (Các file trong Module)

| File | Description |
|------|---------------------|
| [LABS.md](./LABS.md) | Hands-on labs (Bài thực hành) |
| [QUIZ.md](./QUIZ.md) | Knowledge check (Kiểm tra kiến thức) |
| [EXERCISES.md](./EXERCISES.md) | Exercises (Bài tập) |
| [PROJECT.md](./PROJECT.md) | Mini project (Dự án nhỏ) |
| [SOLUTIONS.md](./SOLUTIONS.md) | Solutions (Đáp án) |
| [CHEATSHEET.md](./CHEATSHEET.md) | Quick reference (Tra cứu nhanh) |

---

## 📖 Resources (Tài liệu tham khảo)

- [Jenkins Documentation](https://www.jenkins.io/doc/)
- [Pipeline Syntax Reference](https://www.jenkins.io/doc/book/pipeline/syntax/)
- [Blue Ocean Guide](https://www.jenkins.io/doc/book/blueocean/)

---

<div align="center">

### 🔗 Module Navigation (Điều hướng Module)

| ← Previous | Current | Next → |
|:------------------:|:------------------:|:-------------:|
| [2.2 Docker Compose](../2.2_Docker_Compose/) | **2.3 Jenkins** | [2.4 Kubernetes](../2.4_Kubernetes_Core/) |

---

**Automate your CI/CD! 🔧**

*Tự động hóa CI/CD của bạn!*

</div>
