# 💪 Exercises: Python Basics

> Bài tập tự luyện Python cho DevOps.

---

## 📋 Hướng Dẫn

- Làm bài tập sau khi hoàn thành Labs
- Difficulty: ⭐ Easy, ⭐⭐ Medium, ⭐⭐⭐ Hard
- Xem Solutions sau khi thử tự làm

---

## 📊 Exercise 1: Data Structures ⭐

### Tasks

1. Tạo list `servers` chứa 5 server names
2. Thêm 2 servers mới vào cuối list
3. Xóa server thứ 3
4. Sắp xếp list theo alphabet
5. Tạo dictionary `server_info` mapping server name → IP address
6. In ra tất cả servers có IP bắt đầu bằng "192"

---

## 📝 Exercise 2: String Processing ⭐

### Task

Viết function `parse_log_line(line)` phân tích log line:

Input:

```
"2024-01-15 10:30:00 ERROR Database connection failed"
```

Output:

```python
{
    "date": "2024-01-15",
    "time": "10:30:00",
    "level": "ERROR",
    "message": "Database connection failed"
}
```

---

## 🔄 Exercise 3: File Processing ⭐⭐

### Task

Viết script đọc file `/etc/passwd` (hoặc tạo file giả) và:

1. Đếm số users
2. Liệt kê users có shell là `/bin/bash`
3. Tìm users có UID >= 1000
4. Export kết quả ra JSON file

---

## 🌐 Exercise 4: API Client ⭐⭐

### Task

Viết class `GitHubClient` với methods:

```python
class GitHubClient:
    def get_user(self, username) -> dict:
        """Get user info"""
        pass
    
    def get_repos(self, username) -> list:
        """Get user's public repos"""
        pass
    
    def get_repo_languages(self, owner, repo) -> dict:
        """Get languages used in a repo"""
        pass
```

Test với real GitHub API.

---

## 🔧 Exercise 5: Config Parser ⭐⭐

### Task

Viết function đọc config từ nhiều sources với priority:

1. Default values (lowest)
2. Config file (YAML)
3. Environment variables
4. Command line args (highest)

```python
def load_config(config_file, cli_args) -> dict:
    """
    Returns merged config with proper priority.
    """
    pass
```

---

## 📊 Exercise 6: Log Aggregator ⭐⭐⭐

### Task

Viết script phân tích multiple log files:

Features:

- Đọc tất cả `.log` files trong folder
- Aggregate errors by type
- Generate HTML report với:
  - Pie chart (text-based) của error types
  - Timeline của errors
  - Top 10 frequent errors

---

## 🖥️ Exercise 7: Server Monitor ⭐⭐⭐

### Task

Viết class `ServerMonitor`:

```python
class ServerMonitor:
    def __init__(self, servers: list):
        pass
    
    def check_ping(self, host) -> bool:
        """Check if host responds to ping"""
        pass
    
    def check_port(self, host, port) -> bool:
        """Check if port is open"""
        pass
    
    def check_http(self, url) -> dict:
        """Check HTTP endpoint, return status + response time"""
        pass
    
    def run_all_checks(self) -> list:
        """Run all checks on all servers"""
        pass
    
    def generate_report(self) -> str:
        """Generate markdown report"""
        pass
```

---

## 🔐 Exercise 8: Password Generator ⭐

### Task

Viết CLI tool tạo secure passwords:

```bash
python password_gen.py --length 16 --uppercase --lowercase --digits --special
```

Features:

- Configurable length
- Include/exclude character types
- Copy to clipboard (optional)
- Check against common passwords list

---

## 📦 Exercise 9: Backup Script ⭐⭐

### Task

Viết backup script với features:

```python
def backup_directory(
    source: str,
    destination: str,
    compress: bool = True,
    exclude_patterns: list = None,
    max_backups: int = 5
) -> str:
    """
    Backup a directory.
    
    Returns path to backup file.
    Rotates old backups (keeps max_backups).
    """
    pass
```

---

## 🚀 Exercise 10: Deployment Script ⭐⭐⭐

### Task

Viết deployment automation:

```python
class Deployer:
    def __init__(self, config_file: str):
        pass
    
    def validate_config(self) -> bool:
        """Validate deployment configuration"""
        pass
    
    def pre_deploy_checks(self) -> bool:
        """Run pre-deployment checks"""
        pass
    
    def deploy(self, version: str, environment: str) -> bool:
        """
        Execute deployment:
        1. Pull latest code
        2. Run tests
        3. Build application
        4. Stop old version
        5. Deploy new version
        6. Health check
        7. Rollback if failed
        """
        pass
    
    def rollback(self, version: str) -> bool:
        """Rollback to previous version"""
        pass
```

---

## 📝 Checklist

- [ ] Exercise 1: Data Structures
- [ ] Exercise 2: String Processing
- [ ] Exercise 3: File Processing
- [ ] Exercise 4: API Client
- [ ] Exercise 5: Config Parser
- [ ] Exercise 6: Log Aggregator
- [ ] Exercise 7: Server Monitor
- [ ] Exercise 8: Password Generator
- [ ] Exercise 9: Backup Script
- [ ] Exercise 10: Deployment Script

---

**[← Back to README](./README.md)** | **[View Solutions →](./SOLUTIONS.md)**
