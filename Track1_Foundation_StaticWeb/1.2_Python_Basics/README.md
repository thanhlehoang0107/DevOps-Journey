# 🐍 Module 1.2: Python Basics

[![Duration](https://img.shields.io/badge/Duration-1%20week-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Beginner-green?style=flat-square)](.)

> **Python cho DevOps** - Scripting và automation với Python.

---

## 🎯 Learning Objectives

Sau module này, bạn sẽ:

- ✅ Hiểu Python syntax và data types
- ✅ Làm việc với files và directories
- ✅ Xử lý JSON và YAML configs
- ✅ Gọi APIs với requests library
- ✅ Execute system commands
- ✅ Viết automation scripts

---

## 📋 Prerequisites

- Hoàn thành Module 1.1 Linux & Bash
- Python 3.8+ installed
- VS Code với Python extension

---

## 📚 Content

### 1. Python Basics

#### Data Types

```python
# Strings
name = "DevOps"
path = '/etc/nginx/nginx.conf'

# Numbers
port = 8080
percentage = 99.5

# Boolean
enabled = True
running = False

# Lists
servers = ["web1", "web2", "db1"]
ports = [80, 443, 3306]

# Dictionaries
config = {
    "host": "localhost",
    "port": 8080,
    "debug": True
}
```

#### Control Flow

```python
# If/Else
if status == 200:
    print("OK")
elif status == 404:
    print("Not Found")
else:
    print("Error")

# For loops
for server in servers:
    print(f"Checking {server}")

# While loops
while retries < 3:
    try_connect()
    retries += 1
```

---

### 2. Functions

```python
def deploy_app(app_name, environment="staging"):
    """Deploy application to specified environment."""
    print(f"Deploying {app_name} to {environment}")
    # deployment logic
    return True

# Usage
deploy_app("my-app")
deploy_app("my-app", environment="production")
```

---

### 3. File Operations

```python
# Read file
with open("/etc/hosts", "r") as f:
    content = f.read()
    print(content)

# Write file
with open("output.txt", "w") as f:
    f.write("Hello DevOps!")

# JSON
import json

with open("config.json", "r") as f:
    config = json.load(f)

with open("output.json", "w") as f:
    json.dump(data, f, indent=2)

# YAML
import yaml

with open("config.yaml", "r") as f:
    config = yaml.safe_load(f)
```

---

### 4. Working with OS

```python
import os
import subprocess

# Environment variables
home = os.environ.get("HOME")
api_key = os.getenv("API_KEY", "default")

# File system
os.path.exists("/etc/nginx")
os.listdir("/var/log")
os.makedirs("new/nested/dir", exist_ok=True)

# Run commands
result = subprocess.run(
    ["ls", "-la"],
    capture_output=True,
    text=True
)
print(result.stdout)
```

---

### 5. HTTP Requests

```python
import requests

# GET request
response = requests.get("https://api.github.com")
data = response.json()

# POST request
payload = {"name": "new-server"}
response = requests.post(
    "https://api.example.com/servers",
    json=payload,
    headers={"Authorization": "Bearer token"}
)

# Error handling
response.raise_for_status()
```

---

### 6. Error Handling

```python
try:
    result = risky_operation()
except ValueError as e:
    print(f"Value error: {e}")
except Exception as e:
    print(f"Unexpected error: {e}")
finally:
    cleanup()
```

---

### 7. Classes (OOP)

```python
class Server:
    def __init__(self, hostname, ip):
        self.hostname = hostname
        self.ip = ip
        self.status = "stopped"
    
    def start(self):
        self.status = "running"
        print(f"{self.hostname} started")
    
    def stop(self):
        self.status = "stopped"
        print(f"{self.hostname} stopped")

# Usage
web1 = Server("web1", "192.168.1.10")
web1.start()
```

---

## 🛠️ Common DevOps Patterns

### Config Parser

```python
import yaml
import os

def load_config(config_file):
    """Load config with environment variable override."""
    with open(config_file) as f:
        config = yaml.safe_load(f)
    
    # Override with env vars
    if os.getenv("DB_HOST"):
        config["database"]["host"] = os.getenv("DB_HOST")
    
    return config
```

### Log Parser

```python
def parse_logs(log_file):
    """Parse log file and count errors."""
    errors = []
    
    with open(log_file) as f:
        for line in f:
            if "ERROR" in line:
                errors.append(line.strip())
    
    return errors
```

### Health Checker

```python
import requests

def check_health(urls):
    """Check health of multiple endpoints."""
    results = {}
    
    for url in urls:
        try:
            r = requests.get(url, timeout=5)
            results[url] = r.status_code == 200
        except:
            results[url] = False
    
    return results
```

---

## 📖 Resources

### Documentation

- [Python Official Docs](https://docs.python.org/3/)
- [Requests Library](https://requests.readthedocs.io/)
- [PyYAML](https://pyyaml.org/wiki/PyYAMLDocumentation)

### Books

- "Automate the Boring Stuff with Python"
- "Python for DevOps" by Noah Gift

---

## 🔗 Module Navigation

| Previous | Current | Next |
|----------|---------|------|
| [1.1 Linux & Bash](../1.1_Linux_Bash/) | **1.2 Python** | [1.3 Network](../1.3_Network_Basics/) |

---

## 📝 Module Files

| File | Description |
|------|-------------|
| [LABS.md](./LABS.md) | Hands-on labs |
| [QUIZ.md](./QUIZ.md) | Knowledge check |
| [EXERCISES.md](./EXERCISES.md) | Practice exercises |
| [PROJECT.md](./PROJECT.md) | Mini project |
| [SOLUTIONS.md](./SOLUTIONS.md) | Exercise solutions |
| [CHEATSHEET.md](./CHEATSHEET.md) | Quick reference |

---

<div align="center">

**Ready to automate with Python! 🐍**

</div>
