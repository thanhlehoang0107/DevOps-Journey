# 🔧 Module 2.3: Jenkins

[![Duration](https://img.shields.io/badge/Duration-1%20week-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Intermediate-orange?style=flat-square)](.)

> **CI/CD với Jenkins** - Build automation server.

---

## 🎯 Learning Objectives

- ✅ Install và configure Jenkins
- ✅ Create Jenkins pipelines
- ✅ Jenkinsfile syntax
- ✅ Pipeline as Code
- ✅ Integrate với Docker và Git
- ✅ Blue Ocean interface

---

## 📚 Content

### 1. Jenkins Installation

```bash
# Docker
docker run -d -p 8080:8080 -p 50000:50000 \
  -v jenkins_home:/var/jenkins_home \
  --name jenkins \
  jenkins/jenkins:lts
```

### 2. Pipeline Basics

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
// Declarative
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

// Scripted
node {
    stage('Build') {
        echo 'Building...'
    }
}
```

### 4. Docker Integration

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

## 📝 Module Files

| File | Description |
|------|-------------|
| [LABS.md](./LABS.md) | Hands-on labs |
| [QUIZ.md](./QUIZ.md) | Knowledge check |
| [EXERCISES.md](./EXERCISES.md) | Exercises |
| [PROJECT.md](./PROJECT.md) | Mini project |
| [SOLUTIONS.md](./SOLUTIONS.md) | Solutions |
| [CHEATSHEET.md](./CHEATSHEET.md) | Quick reference |
