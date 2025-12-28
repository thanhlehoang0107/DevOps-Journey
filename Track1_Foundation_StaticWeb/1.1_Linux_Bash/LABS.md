# 🧪 Labs - Linux & Bash

> Bài thực hành hands-on để củng cố kiến thức

---

## 📋 Hướng dẫn thực hiện

1. **Môi trường**: Sử dụng WSL2 (Windows), Terminal (macOS), hoặc Linux VM
2. **Thời gian**: Mỗi lab ~15-30 phút
3. **Ghi chép**: Ghi lại các lệnh đã dùng để review sau

---

## Lab 1: Khám phá File System 🗂️

**Mục tiêu**: Làm quen với cấu trúc thư mục Linux

### Bước 1: Kiểm tra vị trí hiện tại

```bash
pwd
```

**Kết quả mong đợi**: `/home/username` hoặc tương tự

### Bước 2: Liệt kê thư mục gốc

```bash
ls /
```

**Quan sát**: Bạn thấy những thư mục nào?

### Bước 3: Khám phá các thư mục quan trọng

```bash
# Thư mục cấu hình
ls /etc | head -20

# Thư mục logs
ls /var/log

# Thư mục tạm
ls /tmp
```

### Bước 4: Di chuyển qua các thư mục

```bash
cd /var/log
pwd
ls -la

cd /etc
pwd
ls nginx/    # Sẽ báo lỗi nếu chưa cài nginx

cd ~
pwd          # Về home
```

### ✅ Checklist

- [ ] Biết vị trí hiện tại bằng `pwd`
- [ ] Liệt kê được contents với `ls`
- [ ] Di chuyển được bằng `cd`
- [ ] Hiểu sự khác biệt giữa `/`, `/home`, `/etc`, `/var`

---

## Lab 2: Thao tác Files và Directories 📁

**Mục tiêu**: Tạo, copy, move, xóa files và directories

### Bước 1: Tạo cấu trúc project

```bash
cd ~
mkdir -p devops-lab/project1/src
mkdir -p devops-lab/project1/docs
mkdir -p devops-lab/project1/tests
```

### Bước 2: Kiểm tra cấu trúc

```bash
ls -R devops-lab/
```

**Kết quả**:

```
devops-lab/:
project1

devops-lab/project1:
docs  src  tests
```

### Bước 3: Tạo files

```bash
cd devops-lab/project1

# Tạo file rỗng
touch README.md

# Tạo file với nội dung
echo "# My DevOps Project" > README.md
echo "Version: 1.0" >> README.md

# Tạo files trong src
echo 'echo "Hello World"' > src/main.sh
echo '# utility functions' > src/utils.sh
```

### Bước 4: Xem nội dung files

```bash
cat README.md
cat src/main.sh
```

### Bước 5: Copy và Move files

```bash
# Copy file
cp README.md docs/README_backup.md

# Move file
mv src/utils.sh src/helpers.sh

# Kiểm tra
ls -la docs/
ls -la src/
```

### Bước 6: Xóa files (cẩn thận!)

```bash
# Tạo file tạm để xóa
touch temp_file.txt
ls

# Xóa file
rm temp_file.txt
ls

# Xóa thư mục
mkdir to_delete
rm -r to_delete
```

### ✅ Checklist

- [ ] Tạo được thư mục lồng nhau với `mkdir -p`
- [ ] Tạo files với `touch` và `echo`
- [ ] Copy với `cp`, move với `mv`
- [ ] Xóa an toàn với `rm`

---

## Lab 3: Tìm kiếm Files 🔍

**Mục tiêu**: Sử dụng `find` và `grep`

### Setup

```bash
cd ~/devops-lab/project1
echo "This is a test file with ERROR" > logs/error.log 2>/dev/null || mkdir logs && echo "This is a test file with ERROR" > logs/error.log
echo "INFO: Application started" >> logs/error.log
echo "ERROR: Connection failed" >> logs/error.log
echo "INFO: Retrying..." >> logs/error.log
echo "ERROR: Timeout exceeded" >> logs/error.log
```

### Bước 1: Tìm files với find

```bash
# Tìm tất cả .sh files
find . -name "*.sh"

# Tìm tất cả .md files
find . -name "*.md"

# Tìm tất cả directories
find . -type d
```

### Bước 2: Tìm trong nội dung với grep

```bash
# Tìm dòng chứa ERROR
grep "ERROR" logs/error.log

# Hiển thị số dòng
grep -n "ERROR" logs/error.log

# Tìm không phân biệt hoa thường
grep -i "error" logs/error.log

# Đếm số lần xuất hiện
grep -c "ERROR" logs/error.log
```

### Bước 3: Kết hợp find và grep

```bash
# Tìm tất cả files chứa "echo"
grep -r "echo" .

# Chỉ hiển thị tên file
grep -rl "echo" .
```

### ✅ Checklist

- [ ] Tìm files theo tên với `find`
- [ ] Tìm nội dung với `grep`
- [ ] Sử dụng các options: `-n`, `-i`, `-c`, `-r`

---

## Lab 4: Permissions 🔐

**Mục tiêu**: Hiểu và thay đổi file permissions

### Bước 1: Xem permissions hiện tại

```bash
cd ~/devops-lab/project1
ls -la
ls -la src/
```

### Bước 2: Tạo script và kiểm tra permission

```bash
# Tạo script
echo '#!/bin/bash
echo "Hello from script!"
date' > src/myscript.sh

# Xem permission
ls -l src/myscript.sh

# Thử chạy (sẽ báo lỗi Permission denied)
./src/myscript.sh
```

### Bước 3: Thêm execute permission

```bash
# Thêm execute cho owner
chmod u+x src/myscript.sh

# Kiểm tra lại
ls -l src/myscript.sh

# Chạy script
./src/myscript.sh
```

### Bước 4: Thực hành với numeric mode

```bash
# Tạo file mới
touch src/secret.txt
echo "Top secret data" > src/secret.txt

# Chỉ owner đọc ghi (600)
chmod 600 src/secret.txt
ls -l src/secret.txt

# Mọi người đọc được, owner ghi được (644)
chmod 644 src/secret.txt
ls -l src/secret.txt

# Script executable (755)
chmod 755 src/myscript.sh
ls -l src/myscript.sh
```

### ✅ Checklist

- [ ] Đọc được permissions từ `ls -l`
- [ ] Thêm/bớt permission với symbolic mode (`chmod u+x`)
- [ ] Set permissions với numeric mode (`chmod 755`)
- [ ] Hiểu ý nghĩa của 644, 755, 600

---

## Lab 5: Viết Bash Script đầu tiên 📝

**Mục tiêu**: Tạo script tự động hóa

### Bước 1: Script cơ bản

```bash
cd ~/devops-lab/project1

cat > scripts/hello.sh << 'EOF'
#!/bin/bash
# Script: hello.sh
# Mô tả: Script đầu tiên

echo "🚀 Welcome to DevOps Journey!"
echo "📅 Hôm nay là: $(date)"
echo "👤 User hiện tại: $USER"
echo "📂 Thư mục hiện tại: $(pwd)"
EOF

mkdir -p scripts
chmod +x scripts/hello.sh
./scripts/hello.sh
```

### Bước 2: Script với biến và input

```bash
cat > scripts/greet.sh << 'EOF'
#!/bin/bash
# Script hỏi tên và chào

echo "Bạn tên là gì?"
read NAME

echo "Xin chào, $NAME! 👋"
echo "Chào mừng đến với DevOps Journey"
EOF

chmod +x scripts/greet.sh
./scripts/greet.sh
```

### Bước 3: Script với điều kiện

```bash
cat > scripts/check_docker.sh << 'EOF'
#!/bin/bash
# Kiểm tra Docker đã cài đặt chưa

if command -v docker &> /dev/null; then
    echo "✅ Docker đã được cài đặt"
    docker --version
else
    echo "❌ Docker chưa được cài đặt"
    echo "Hãy cài đặt Docker theo hướng dẫn trong Setup_Environment"
fi
EOF

chmod +x scripts/check_docker.sh
./scripts/check_docker.sh
```

### Bước 4: Script với vòng lặp

```bash
cat > scripts/countdown.sh << 'EOF'
#!/bin/bash
# Đếm ngược

echo "🚀 Khởi động trong..."

for i in 5 4 3 2 1; do
    echo "$i..."
    sleep 1
done

echo "🎉 BLAST OFF!"
EOF

chmod +x scripts/countdown.sh
./scripts/countdown.sh
```

### ✅ Checklist

- [ ] Tạo được script với shebang `#!/bin/bash`
- [ ] Sử dụng biến và đọc input
- [ ] Sử dụng điều kiện `if/else`
- [ ] Sử dụng vòng lặp `for`

---

## Lab 6: System Health Check Script 💊

**Mục tiêu**: Tạo script thực tế để kiểm tra hệ thống

### Tạo script hoàn chỉnh

```bash
cat > scripts/system_health.sh << 'EOF'
#!/bin/bash
###########################################
# System Health Check Script
# Mô tả: Kiểm tra tình trạng hệ thống
###########################################

echo "========================================"
echo "    🏥 SYSTEM HEALTH CHECK REPORT"
echo "========================================"
echo ""

# Thông tin hệ thống
echo "📋 THÔNG TIN HỆ THỐNG"
echo "----------------------------------------"
echo "Hostname: $(hostname)"
echo "Kernel: $(uname -r)"
echo "Thời gian: $(date)"
echo ""

# CPU và Memory
echo "💻 CPU & MEMORY"
echo "----------------------------------------"
echo "CPU cores: $(nproc)"
echo "Memory:"
free -h | grep -E "Mem|Swap"
echo ""

# Disk Usage
echo "💾 DISK USAGE"
echo "----------------------------------------"
df -h | grep -E "Filesystem|/$"
echo ""

# Top Processes
echo "🔝 TOP 5 PROCESSES (by CPU)"
echo "----------------------------------------"
ps aux --sort=-%cpu | head -6
echo ""

# Network
echo "🌐 NETWORK"
echo "----------------------------------------"
echo "IP Addresses:"
ip addr show 2>/dev/null | grep "inet " || hostname -I
echo ""

# Docker (nếu có)
echo "🐳 DOCKER STATUS"
echo "----------------------------------------"
if command -v docker &> /dev/null; then
    if docker info &> /dev/null; then
        echo "Docker: Running ✅"
        echo "Containers: $(docker ps -q | wc -l) running"
        echo "Images: $(docker images -q | wc -l) available"
    else
        echo "Docker: Installed but not running ⚠️"
    fi
else
    echo "Docker: Not installed ❌"
fi

echo ""
echo "========================================"
echo "    Report completed at $(date +%H:%M:%S)"
echo "========================================"
EOF

chmod +x scripts/system_health.sh
./scripts/system_health.sh
```

### ✅ Lab hoàn thành

- [ ] Script chạy thành công
- [ ] Hiển thị thông tin hệ thống
- [ ] Kiểm tra Docker status

---

## 🎯 Thử thách bổ sung

Sau khi hoàn thành các labs, thử:

1. **Sửa đổi `system_health.sh`** để ghi output ra file log
2. **Tạo script** liệt kê tất cả files >10MB trong home directory
3. **Tạo script** backup thư mục project vào folder backup với timestamp

---

## 🔗 Navigation

[⬅️ README](./README.md) | [CHEATSHEET](./CHEATSHEET.md) | [QUIZ ➡️](./QUIZ.md)

---

*Cập nhật: 2025-12-29*
