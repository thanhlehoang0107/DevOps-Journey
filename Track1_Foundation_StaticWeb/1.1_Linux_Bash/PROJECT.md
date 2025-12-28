# 🎯 Project: Linux & Bash

> Mini project để áp dụng kiến thức Linux và Bash scripting.

---

## 📋 Project Overview

### Project Name: **Server Monitoring Dashboard Script**

Xây dựng một bộ scripts để monitor và report trạng thái server.

### Objectives

- Áp dụng kiến thức Bash scripting
- Làm việc với system commands
- Xử lý text và tạo reports
- Automation với cron jobs

### Duration: 2-3 ngày

---

## 🎯 Requirements

### Core Features

#### 1. System Information Collector (`collect_info.sh`)

Script thu thập thông tin hệ thống:

```
Output format:
=====================================
SYSTEM REPORT - 2024-01-15 10:30:00
=====================================

HOSTNAME: my-server
OS: Ubuntu 22.04 LTS
KERNEL: 5.15.0-91-generic
UPTIME: 5 days, 3 hours, 25 minutes

CPU:
  Model: Intel(R) Core(TM) i7-9700 CPU @ 3.00GHz
  Cores: 8
  Usage: 15%

MEMORY:
  Total: 16 GB
  Used: 8 GB (50%)
  Free: 8 GB

DISK:
  /       : 45% used (45GB / 100GB)
  /home   : 60% used (120GB / 200GB)

NETWORK:
  eth0: 192.168.1.100
  
TOP 5 PROCESSES (by CPU):
  PID    CPU%   MEM%   COMMAND
  1234   25.0   5.0    nginx
  ...
=====================================
```

#### 2. Health Checker (`health_check.sh`)

Script kiểm tra "sức khỏe" server:

- [ ] CPU usage < 80%
- [ ] Memory usage < 90%
- [ ] Disk usage < 85%
- [ ] Required services running (nginx, docker)
- [ ] Network connectivity (ping 8.8.8.8)
- [ ] DNS resolution working

```
Output:
[✓] CPU Usage: 15% (OK)
[✓] Memory Usage: 50% (OK)
[✓] Disk Usage: 45% (OK)
[✓] Service nginx: running
[✗] Service docker: stopped  ← ALERT!
[✓] Network: OK
[✓] DNS: OK

Status: WARNING - 1 issue found
```

#### 3. Log Analyzer (`analyze_logs.sh`)

Script phân tích log files:

Input: Log file path
Output:

- Tổng số entries
- Breakdown by log level (INFO, WARNING, ERROR)
- Top 5 error messages
- Timeline (entries per hour)

#### 4. Alert System (`alert.sh`)

Script gửi alerts khi có vấn đề:

- Ghi alerts vào file `/var/log/server_alerts.log`
- (Optional) Gửi email notification
- Include timestamp và severity level

#### 5. Main Dashboard (`dashboard.sh`)

Script chính tích hợp tất cả:

```bash
./dashboard.sh [options]

Options:
  -i, --info      Show system information
  -h, --health    Run health check
  -l, --logs      Analyze logs
  -a, --all       Run all checks
  -w, --watch     Continuous monitoring (refresh every 5s)
  --help          Show help
```

---

## 📁 Project Structure

```
server-monitor/
├── scripts/
│   ├── collect_info.sh
│   ├── health_check.sh
│   ├── analyze_logs.sh
│   ├── alert.sh
│   └── dashboard.sh
├── config/
│   ├── thresholds.conf    # CPU_THRESHOLD=80, etc.
│   └── services.conf      # List of services to monitor
├── logs/
│   └── .gitkeep
├── reports/
│   └── .gitkeep
├── install.sh             # Installation script
├── uninstall.sh          # Cleanup script
└── README.md
```

---

## 📝 Detailed Specifications

### `thresholds.conf`

```bash
# Alert thresholds
CPU_THRESHOLD=80
MEMORY_THRESHOLD=90
DISK_THRESHOLD=85

# Services to monitor
SERVICES="nginx docker ssh"

# Log paths
SYSTEM_LOG=/var/log/syslog
APP_LOG=/var/log/app.log

# Alert settings
ALERT_LOG=/var/log/server_alerts.log
```

### `collect_info.sh` Specifications

```bash
#!/bin/bash

# Functions needed:
# - get_hostname()
# - get_os_info()
# - get_kernel_version()
# - get_uptime()
# - get_cpu_info()
# - get_memory_info()
# - get_disk_info()
# - get_network_info()
# - get_top_processes()
# - generate_report()

# Output options:
# - Terminal (colored)
# - File (plain text)
# - JSON format (optional bonus)
```

### `health_check.sh` Specifications

```bash
#!/bin/bash

# Exit codes:
# 0 = All checks passed
# 1 = Warning (non-critical issues)
# 2 = Critical (immediate attention needed)

# Check functions:
# - check_cpu()
# - check_memory()
# - check_disk()
# - check_services()
# - check_network()
# - check_dns()

# Each function returns:
# 0 = OK
# 1 = Warning
# 2 = Critical
```

---

## ✅ Acceptance Criteria

### Must Have

- [ ] All 5 scripts working correctly
- [ ] Proper error handling
- [ ] Colored terminal output
- [ ] Help messages for all scripts
- [ ] Configuration file support
- [ ] Exit codes appropriate

### Should Have

- [ ] Logging of script activities
- [ ] Report generation (text files)
- [ ] Watch mode với refresh
- [ ] Installation script

### Nice to Have

- [ ] JSON output option
- [ ] Email alerts
- [ ] Historical data storage
- [ ] Simple web dashboard (bonus)

---

## 🔧 Technical Requirements

### Bash Version

- Bash 4.0+ required

### Permissions

- Some commands need sudo (e.g., reading system logs)
- Handle permission errors gracefully

### Portability

- Should work on Ubuntu 20.04+
- Handle missing commands (check if command exists)

### Code Quality

- Use functions for modularity
- Include comments
- Consistent coding style
- No hardcoded values (use config)

---

## 📊 Evaluation Rubric

| Criteria | Points |
|----------|--------|
| **Functionality** (scripts work correctly) | 40 |
| **Code Quality** (clean, readable, documented) | 20 |
| **Error Handling** (graceful failures) | 15 |
| **Configuration** (flexible, no hardcoding) | 10 |
| **User Experience** (helpful messages, colors) | 10 |
| **Bonus Features** | 5 |
| **Total** | **100** |

### Grading

- 90-100: Excellent
- 80-89: Good
- 70-79: Satisfactory
- Below 70: Needs improvement

---

## 🚀 Getting Started

### Step 1: Setup

```bash
# Create project directory
mkdir -p ~/server-monitor/{scripts,config,logs,reports}
cd ~/server-monitor

# Create config file
cat << 'EOF' > config/thresholds.conf
CPU_THRESHOLD=80
MEMORY_THRESHOLD=90
DISK_THRESHOLD=85
SERVICES="nginx ssh"
EOF
```

### Step 2: Start Simple

```bash
# Begin with collect_info.sh
touch scripts/collect_info.sh
chmod +x scripts/collect_info.sh

# Start with basic structure
cat << 'EOF' > scripts/collect_info.sh
#!/bin/bash
# System Information Collector

echo "Starting system info collection..."
# Your code here
EOF
```

### Step 3: Iterate

- Implement one function at a time
- Test frequently
- Commit progress to git

---

## 💡 Hints

### Getting System Info

```bash
# Hostname
hostname

# OS info
cat /etc/os-release

# CPU usage
top -bn1 | grep "Cpu(s)"

# Memory
free -h

# Disk
df -h
```

### Colored Output

```bash
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
NC='\033[0m' # No Color

echo -e "${GREEN}[✓]${NC} Check passed"
echo -e "${RED}[✗]${NC} Check failed"
```

### Service Check

```bash
systemctl is-active --quiet nginx && echo "running" || echo "stopped"
```

---

## 📥 Submission

### Required Files

1. All script files
2. Config files
3. README.md với instructions
4. Sample output/screenshots

### Submission Format

```bash
# Create archive
tar -czvf server-monitor-yourname.tar.gz server-monitor/
```

---

## 🔗 Resources

- [CHEATSHEET.md](./CHEATSHEET.md) - Command reference
- [LABS.md](./LABS.md) - Review labs
- [SOLUTIONS.md](./SOLUTIONS.md) - Example solutions

---

**Good luck! 🚀**
