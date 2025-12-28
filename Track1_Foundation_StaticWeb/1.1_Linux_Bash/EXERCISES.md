# 💪 Exercises: Linux & Bash

> Bài tập tự luyện để củng cố kiến thức Linux và Bash scripting.

---

## 📋 Hướng Dẫn

- Làm bài tập **sau khi hoàn thành Labs**
- Thử tự làm trước khi xem Solutions
- Mỗi bài có **difficulty level**: ⭐ Easy, ⭐⭐ Medium, ⭐⭐⭐ Hard

---

## 🗂️ Exercise 1: File System Navigation ⭐

### Yêu cầu

Thực hiện các task sau và ghi lại commands đã dùng:

1. Tạo cấu trúc thư mục sau:

```
~/devops-practice/
├── projects/
│   ├── web-app/
│   │   ├── src/
│   │   ├── tests/
│   │   └── docs/
│   └── api-server/
│       ├── src/
│       └── tests/
├── scripts/
└── logs/
```

1. Tạo file `README.md` trong mỗi thư mục `src/`
2. Tạo 5 files log giả trong `logs/`: `app-01.log` đến `app-05.log`
3. Di chuyển tất cả files `.log` vào thư mục mới `logs/archive/`
4. Xóa thư mục `api-server/tests/` (chú ý: thư mục trống)

### Verification

```bash
# Kiểm tra cấu trúc
tree ~/devops-practice/
```

---

## 🔐 Exercise 2: Permissions Management ⭐⭐

### Yêu cầu

1. Tạo file `secret.txt` với nội dung "This is confidential"
2. Tạo file `public.txt` với nội dung "This is public"
3. Tạo script `deploy.sh` với nội dung:

   ```bash
   #!/bin/bash
   echo "Deploying application..."
   ```

4. Thiết lập permissions:
   - `secret.txt`: Chỉ owner đọc được (400)
   - `public.txt`: Ai cũng đọc được, chỉ owner sửa được (644)
   - `deploy.sh`: Owner full quyền, group và others chỉ execute (711)

5. Tạo group `devteam` và thêm user hiện tại vào group
6. Thay đổi group owner của `deploy.sh` thành `devteam`

### Verification

```bash
ls -la secret.txt public.txt deploy.sh
```

---

## 🔍 Exercise 3: Text Processing ⭐⭐

### Setup

Tạo file `server.log` với nội dung:

```bash
cat << 'EOF' > server.log
2024-01-15 08:00:01 INFO Server started
2024-01-15 08:05:23 INFO User login: admin
2024-01-15 08:10:45 WARNING High memory usage: 85%
2024-01-15 08:15:00 ERROR Database connection failed
2024-01-15 08:15:30 INFO Retrying database connection
2024-01-15 08:15:35 INFO Database connected
2024-01-15 08:20:00 INFO User login: john
2024-01-15 08:25:00 ERROR API timeout
2024-01-15 08:30:00 INFO User login: admin
2024-01-15 08:35:00 WARNING Disk space low: 90%
2024-01-15 08:40:00 INFO User logout: john
2024-01-15 08:45:00 ERROR Connection reset
2024-01-15 08:50:00 INFO Backup completed
EOF
```

### Tasks

1. Đếm số dòng ERROR trong file
2. Liệt kê tất cả unique users đã login
3. Hiển thị chỉ timestamp và message của các WARNING
4. Tìm dòng cuối cùng chứa "admin"
5. Thay thế tất cả "INFO" thành "[INFO]" và lưu vào file mới
6. Hiển thị 5 dòng đầu tiên
7. Đếm số lần từ "connection" xuất hiện (case-insensitive)

---

## 📊 Exercise 4: Process Management ⭐⭐

### Tasks

1. Liệt kê top 5 processes sử dụng nhiều CPU nhất
2. Liệt kê top 5 processes sử dụng nhiều RAM nhất
3. Tìm tất cả processes của user hiện tại
4. Chạy command `sleep 300` trong background
5. Tìm PID của process `sleep` vừa chạy
6. Gửi signal SIGTERM đến process đó

### Bonus

- Viết one-liner để kill tất cả processes có tên chứa "sleep"

---

## 🔧 Exercise 5: Bash Scripting Basics ⭐⭐

### Task 1: System Info Script

Viết script `sysinfo.sh` hiển thị:

- Hostname
- OS version
- Kernel version
- CPU info (model name)
- Total RAM
- Disk usage của /
- Current date/time
- Uptime

### Task 2: User Input Script

Viết script `greet.sh`:

- Nhận input tên người dùng
- In ra lời chào theo thời gian trong ngày:
  - 5:00 - 11:59 → "Good morning"
  - 12:00 - 17:59 → "Good afternoon"
  - 18:00 - 21:59 → "Good evening"
  - 22:00 - 4:59 → "Good night"

### Task 3: File Counter Script

Viết script `counter.sh`:

- Nhận argument là đường dẫn thư mục
- Đếm và in ra:
  - Số files
  - Số directories
  - Số hidden files/dirs

---

## 🔄 Exercise 6: Loops and Conditions ⭐⭐⭐

### Task 1: Backup Script

Viết script `backup.sh`:

- Nhận 2 arguments: source_dir và backup_dir
- Kiểm tra source_dir tồn tại
- Tạo backup_dir nếu chưa có
- Copy tất cả files từ source sang backup
- Thêm timestamp vào tên backup folder
- In summary: số files đã backup

### Task 2: Log Rotator

Viết script `rotate.sh`:

- Nhận argument là thư mục chứa logs
- Với mỗi file `.log`:
  - Nếu size > 1MB: nén thành `.gz` và xóa original
  - Nếu file đã là `.gz` và cũ hơn 7 ngày: xóa
- In summary sau khi hoàn thành

### Task 3: Service Checker

Viết script `check_services.sh`:

- Định nghĩa array các services: nginx, docker, ssh
- Loop qua từng service
- Kiểm tra status (running/stopped)
- In ra table với status của từng service
- Exit code 1 nếu có service nào stopped

---

## 🌐 Exercise 7: Networking Commands ⭐⭐

### Tasks

1. Hiển thị IP address của tất cả interfaces
2. Kiểm tra port 80 có đang listen không
3. Kiểm tra connectivity đến google.com
4. Trace route đến 8.8.8.8
5. Hiển thị tất cả connections đang ESTABLISHED
6. Tìm process nào đang sử dụng port 22

### Bonus

Viết script kiểm tra connectivity đến list các hosts và report status.

---

## 📦 Exercise 8: Package Management ⭐

### Tasks (Ubuntu/Debian)

1. Update package list
2. Tìm kiếm package `nginx`
3. Hiển thị thông tin về package `curl`
4. Liệt kê tất cả packages đã cài đặt có chứa "python"
5. Kiểm tra xem `git` đã được cài chưa

### Tasks (RHEL/CentOS)

1. Thực hiện tương tự với `yum` hoặc `dnf`

---

## 🔐 Exercise 9: SSH & Remote Operations ⭐⭐⭐

### Prerequisites

- Có access đến một remote server (hoặc dùng localhost)

### Tasks

1. Generate SSH key pair (ed25519)
2. Copy public key đến remote server
3. SSH đến remote và chạy `uptime`
4. Copy file từ local sang remote
5. Copy thư mục từ remote về local
6. Tạo SSH config entry cho remote server

### Bonus

Viết script deploy đơn giản:

- SSH đến server
- Pull code mới từ git
- Restart service

---

## 🎯 Exercise 10: Comprehensive Challenge ⭐⭐⭐

### Scenario

Bạn là DevOps Engineer cần viết automation script cho server mới.

### Requirements

Viết script `server_setup.sh` thực hiện:

1. **System Update**
   - Update package list
   - Upgrade installed packages

2. **User Setup**
   - Tạo user `deploy` nếu chưa tồn tại
   - Thêm user vào group `sudo`
   - Setup SSH key cho user

3. **Security**
   - Cài đặt và enable `ufw`
   - Allow SSH (22), HTTP (80), HTTPS (443)
   - Deny all other incoming

4. **Software Installation**
   - Cài đặt: git, docker, nginx
   - Enable và start docker, nginx

5. **Directory Setup**
   - Tạo `/opt/apps` với owner `deploy`
   - Tạo `/var/log/apps` với proper permissions

6. **Logging**
   - Log tất cả actions vào `/var/log/setup.log`
   - Include timestamps

7. **Verification**
   - Kiểm tra mỗi step
   - Print summary ở cuối

### Bonus Features

- Dry-run mode (--dry-run flag)
- Verbose mode (-v flag)
- Skip steps nếu đã hoàn thành

---

## 📝 Submission Checklist

Sau khi hoàn thành exercises:

- [ ] Exercise 1: File System Navigation
- [ ] Exercise 2: Permissions Management
- [ ] Exercise 3: Text Processing
- [ ] Exercise 4: Process Management
- [ ] Exercise 5: Bash Scripting Basics
- [ ] Exercise 6: Loops and Conditions
- [ ] Exercise 7: Networking Commands
- [ ] Exercise 8: Package Management
- [ ] Exercise 9: SSH & Remote Operations
- [ ] Exercise 10: Comprehensive Challenge

---

## 🔗 Resources

- [SOLUTIONS.md](./SOLUTIONS.md) - Xem đáp án
- [CHEATSHEET.md](./CHEATSHEET.md) - Tra cứu commands
- [LABS.md](./LABS.md) - Review bài thực hành

---

**[← Back to README](./README.md)** | **[View Solutions →](./SOLUTIONS.md)**
