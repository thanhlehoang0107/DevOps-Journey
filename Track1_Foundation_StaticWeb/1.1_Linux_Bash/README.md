# 🐧 Module 1.1: Linux & Bash

[![Duration](https://img.shields.io/badge/Duration-10--15%20hours-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Beginner-green?style=flat-square)](.)

> **Linux Fundamentals & Bash Scripting** - Foundation for every DevOps Engineer.
>
> *Nền tảng Linux & Bash Scripting - Nền tảng cho mọi DevOps Engineer.*

---

## 🎯 Learning Objectives (Mục tiêu học tập)

After this module, you will (Sau module này, bạn sẽ):

- ✅ Understand what Linux is and why DevOps engineers need it (Hiểu Linux là gì và tại sao cần)
- ✅ Navigate the file system proficiently (Điều hướng file system thành thạo)
- ✅ Manipulate files and directories (Thao tác files và thư mục)
- ✅ Manage users, permissions, processes (Quản lý users, permissions, processes)
- ✅ Write basic Bash scripts (Viết Bash script cơ bản)
- ✅ Use package managers - apt/yum (Sử dụng package manager)

---

## 📖 Nội dung

### 1. Linux là gì? (30 phút)

#### 1.1 Giới thiệu

**Linux** là một hệ điều hành mã nguồn mở, được phát triển bởi Linus Torvalds năm 1991. Khác với Windows hay macOS, Linux hoàn toàn miễn phí và có thể tùy chỉnh.

#### 1.2 Tại sao DevOps cần Linux?

| Lý do | Giải thích |
|-------|------------|
| **Servers chạy Linux** | 90%+ servers trên internet chạy Linux |
| **Containers** | Docker, Kubernetes đều dựa trên Linux |
| **Scripting** | Bash scripting là công cụ tự động hóa mạnh mẽ |
| **Free & Open Source** | Không tốn tiền license, dễ customize |

#### 1.3 Các Linux Distributions phổ biến

```
┌─────────────────────────────────────────────────────────────┐
│                    LINUX DISTRIBUTIONS                       │
├────────────────┬────────────────┬────────────────────────────┤
│   Ubuntu/      │   RHEL/        │   Alpine                   │
│   Debian       │   CentOS       │   (Containers)             │
├────────────────┼────────────────┼────────────────────────────┤
│   apt install  │   yum install  │   apk add                  │
│   .deb         │   .rpm         │   Minimal size             │
└────────────────┴────────────────┴────────────────────────────┘
```

---

### 2. Linux File System (1 giờ)

#### 2.1 Cấu trúc thư mục

```
/                    ← Root directory (gốc)
├── home/            ← Thư mục người dùng
│   └── user/        ← Home của user (tương đương C:\Users\username)
├── etc/             ← File cấu hình hệ thống
├── var/             ← Logs, databases
│   └── log/         ← System logs
├── tmp/             ← Files tạm (tự động xóa)
├── opt/             ← Software của bên thứ 3
├── usr/             ← User programs
│   ├── bin/         ← User binaries
│   └── local/       ← Locally installed software
├── bin/             ← Essential binaries
├── sbin/            ← System binaries (admin)
└── root/            ← Home của root user
```

#### 2.2 Absolute vs Relative Paths

```bash
# Absolute Path - Bắt đầu từ /
/home/user/documents/file.txt

# Relative Path - Tương đối với vị trí hiện tại
./documents/file.txt    # Trong thư mục hiện tại
../documents/file.txt   # Lùi 1 cấp rồi vào documents
```

#### 2.3 Những thư mục quan trọng cần nhớ

| Thư mục | Mục đích | Ví dụ |
|---------|----------|-------|
| `/home/user` | Files cá nhân | Documents, Downloads |
| `/etc` | Config files | `/etc/nginx/nginx.conf` |
| `/var/log` | Logs | `/var/log/syslog` |
| `/tmp` | Files tạm | Tự động xóa khi reboot |

---

### 3. Điều hướng cơ bản (1 giờ)

#### 3.1 pwd - Print Working Directory

```bash
$ pwd
/home/devops

# Cho biết bạn đang ở đâu
```

#### 3.2 ls - List Directory Contents

```bash
ls              # Liệt kê files
ls -l           # Chi tiết (long format)
ls -a           # Hiển thị hidden files (bắt đầu bằng .)
ls -la          # Kết hợp cả 2
ls -lh          # Human readable (KB, MB, GB)
ls -lt          # Sắp xếp theo thời gian
```

**Đọc output của `ls -l`:**

```
-rw-r--r-- 1 user group 4096 Dec 29 10:00 file.txt
│          │ │    │     │    │            │
│          │ │    │     │    │            └── Tên file
│          │ │    │     │    └── Thời gian sửa đổi
│          │ │    │     └── Kích thước (bytes)
│          │ │    └── Group owner
│          │ └── User owner
│          └── Số hard links
└── Permissions (rwxrwxrwx)
```

#### 3.3 cd - Change Directory

```bash
cd /path/to/directory    # Đi đến đường dẫn tuyệt đối
cd folder                # Đi vào folder con
cd ..                    # Lùi lên 1 cấp
cd ../..                 # Lùi lên 2 cấp
cd ~                     # Về home directory
cd -                     # Quay lại thư mục trước đó
```

---

### 4. Thao tác Files và Directories (2 giờ)

#### 4.1 Tạo files và thư mục

```bash
# Tạo file rỗng
touch file.txt

# Tạo file với nội dung
echo "Hello World" > file.txt

# Tạo thư mục
mkdir mydir

# Tạo thư mục lồng nhau
mkdir -p parent/child/grandchild
```

#### 4.2 Copy, Move, Rename

```bash
# Copy file
cp source.txt destination.txt
cp source.txt /path/to/destination/

# Copy thư mục (recursive)
cp -r source_dir/ destination_dir/

# Move/Rename file
mv oldname.txt newname.txt
mv file.txt /path/to/destination/

# Move thư mục
mv source_dir/ destination/
```

#### 4.3 Xóa files và thư mục

```bash
# Xóa file
rm file.txt

# Xóa nhiều files
rm file1.txt file2.txt file3.txt
rm *.txt                # Xóa tất cả .txt files

# Xóa thư mục rỗng
rmdir empty_dir/

# Xóa thư mục và nội dung bên trong
rm -r directory/

# Xóa không hỏi (NGUY HIỂM!)
rm -rf directory/

# ⚠️ CẢNH BÁO: Không bao giờ chạy: rm -rf /
```

#### 4.4 Đọc nội dung files

```bash
# Xem toàn bộ file
cat file.txt

# Xem với phân trang (nhấn q để thoát)
less file.txt

# Xem 10 dòng đầu/cuối
head file.txt
head -n 20 file.txt     # 20 dòng đầu
tail file.txt
tail -n 20 file.txt     # 20 dòng cuối

# Theo dõi file realtime (logs)
tail -f /var/log/syslog
```

---

### 5. Tìm kiếm (1 giờ)

#### 5.1 find - Tìm files

```bash
# Tìm theo tên
find /home -name "*.txt"

# Tìm theo type (f=file, d=directory)
find . -type f -name "*.log"
find . -type d -name "config"

# Tìm theo thời gian sửa đổi
find . -mtime -7        # Sửa trong 7 ngày qua
find . -mtime +30       # Sửa hơn 30 ngày trước

# Tìm theo size
find . -size +100M      # Lớn hơn 100MB
find . -size -10K       # Nhỏ hơn 10KB
```

#### 5.2 grep - Tìm kiếm trong nội dung

```bash
# Tìm pattern trong file
grep "error" logfile.txt

# Không phân biệt hoa thường
grep -i "Error" logfile.txt

# Hiển thị số dòng
grep -n "error" logfile.txt

# Tìm đệ quy trong thư mục
grep -r "TODO" ./src/

# Đếm số lần xuất hiện
grep -c "error" logfile.txt
```

#### 5.3 Kết hợp find và grep

```bash
# Tìm files .txt chứa "error"
find . -name "*.txt" -exec grep -l "error" {} \;
```

---

### 6. Permissions (2 giờ)

#### 6.1 Hiểu về Permissions

```
-rwxr-xr--
│└┬─┘└┬─┘└┬─┘
│ │   │   └── Others (o): r-- = read only
│ │   └────── Group (g): r-x = read + execute
│ └────────── User/Owner (u): rwx = full access
└──────────── File type (- = file, d = directory)
```

| Permission | Ký hiệu | Số | Ý nghĩa |
|------------|---------|-----|---------|
| Read | r | 4 | Đọc file/liệt kê thư mục |
| Write | w | 2 | Ghi file/tạo xóa trong thư mục |
| Execute | x | 1 | Chạy file/vào thư mục |

#### 6.2 chmod - Thay đổi permissions

**Cách numeric:**

```bash
chmod 755 script.sh     # rwxr-xr-x
chmod 644 file.txt      # rw-r--r--
chmod 600 secret.txt    # rw------- (chỉ owner đọc ghi)
chmod 777 folder/       # rwxrwxrwx (KHÔNG NÊN!)
```

**Cách symbolic:**

```bash
chmod +x script.sh      # Thêm execute cho tất cả
chmod u+x script.sh     # Thêm execute cho owner
chmod g-w file.txt      # Bỏ write của group
chmod o-rwx secret.txt  # Bỏ hết quyền của others
```

#### 6.3 chown - Thay đổi owner

```bash
sudo chown user:group file.txt
sudo chown -R user:group directory/  # Recursive
```

---

### 7. Quản lý Processes (1.5 giờ)

#### 7.1 Xem processes

```bash
# Liệt kê tất cả processes
ps aux

# Tìm process cụ thể
ps aux | grep nginx

# Xem realtime (nhấn q để thoát)
top
htop    # Phiên bản đẹp hơn (cần cài thêm)
```

#### 7.2 Kill processes

```bash
# Kill bằng PID
kill 1234
kill -9 1234    # Force kill

# Kill bằng tên
pkill nginx
killall nginx
```

#### 7.3 Background processes

```bash
# Chạy trong background
./script.sh &

# Xem background jobs
jobs

# Đưa về foreground
fg %1

# Đưa vào background
bg %1

# Chạy process không bị ảnh hưởng khi đóng terminal
nohup ./long_running_script.sh &
```

---

### 8. Package Manager (1 giờ)

#### 8.1 APT (Ubuntu/Debian)

```bash
# Update danh sách packages
sudo apt update

# Upgrade packages đã cài
sudo apt upgrade

# Cài đặt package
sudo apt install nginx

# Gỡ cài đặt
sudo apt remove nginx
sudo apt autoremove     # Xóa dependencies không dùng

# Tìm package
apt search nginx
```

#### 8.2 YUM/DNF (RHEL/CentOS)

```bash
sudo yum update
sudo yum install nginx
sudo yum remove nginx
yum search nginx
```

---

### 9. Bash Scripting (3 giờ)

#### 9.1 Script đầu tiên

```bash
#!/bin/bash
# File: hello.sh

echo "Hello, DevOps!"
```

Chạy script:

```bash
chmod +x hello.sh
./hello.sh
```

#### 9.2 Biến (Variables)

```bash
#!/bin/bash

# Gán biến (KHÔNG có dấu cách quanh =)
NAME="DevOps"
AGE=25

# Sử dụng biến
echo "Hello, $NAME"
echo "You are $AGE years old"

# Input từ người dùng
echo "Enter your name:"
read USERNAME
echo "Hello, $USERNAME!"
```

#### 9.3 Điều kiện (if/else)

```bash
#!/bin/bash

FILE="/etc/passwd"

if [ -f "$FILE" ]; then
    echo "$FILE exists."
else
    echo "$FILE does not exist."
fi

# Kiểm tra số
NUMBER=10
if [ $NUMBER -gt 5 ]; then
    echo "Greater than 5"
elif [ $NUMBER -eq 5 ]; then
    echo "Equal to 5"
else
    echo "Less than 5"
fi
```

**Operators:**

| Operator | Ý nghĩa |
|----------|---------|
| `-f` | File exists |
| `-d` | Directory exists |
| `-eq` | Equal (số) |
| `-ne` | Not equal |
| `-gt` | Greater than |
| `-lt` | Less than |
| `=` | String equal |
| `!=` | String not equal |

#### 9.4 Vòng lặp (Loops)

```bash
#!/bin/bash

# For loop
for i in 1 2 3 4 5; do
    echo "Number: $i"
done

# For loop với range
for i in {1..10}; do
    echo "Count: $i"
done

# For loop với files
for file in *.txt; do
    echo "Processing: $file"
done

# While loop
COUNT=0
while [ $COUNT -lt 5 ]; do
    echo "Count: $COUNT"
    COUNT=$((COUNT + 1))
done
```

#### 9.5 Functions

```bash
#!/bin/bash

# Định nghĩa function
greet() {
    echo "Hello, $1!"
}

# Gọi function
greet "DevOps"
greet "World"

# Function với return value
add_numbers() {
    local RESULT=$(( $1 + $2 ))
    echo $RESULT
}

SUM=$(add_numbers 5 3)
echo "Sum: $SUM"
```

---

### 10. Pipes và Redirect (1 giờ)

#### 10.1 Pipe (|)

Truyền output của command này làm input cho command khác:

```bash
# Đếm số file trong thư mục
ls -la | wc -l

# Tìm process nginx
ps aux | grep nginx

# Sắp xếp và lấy 10 file lớn nhất
du -h * | sort -rh | head -10
```

#### 10.2 Redirect

```bash
# Ghi output vào file (overwrite)
echo "Hello" > file.txt

# Append vào file
echo "World" >> file.txt

# Redirect stderr
command 2> error.log

# Redirect cả stdout và stderr
command > output.txt 2>&1
command &> all_output.txt
```

---

## 📝 Module Files (Các file trong Module)

| File | Description |
|------|-------------|
| [CHEATSHEET.md](./CHEATSHEET.md) | Quick reference (Tra cứu nhanh) |
| [LABS.md](./LABS.md) | Hands-on labs (Bài thực hành) |
| [QUIZ.md](./QUIZ.md) | Knowledge check (Kiểm tra kiến thức) |
| [EXERCISES.md](./EXERCISES.md) | Exercises (Bài tập) |
| [PROJECT.md](./PROJECT.md) | Mini project (Dự án nhỏ) |
| [SOLUTIONS.md](./SOLUTIONS.md) | Solutions (Đáp án) |

---

<div align="center">

### 🔗 Module Navigation (Điều hướng Module)

| ← Previous | Current | Next → |
|:------------------:|:------------------:|:-------------:|
| [Setup Environment](../../Setup_Environment/) | **1.1 Linux & Bash** | [1.2 Python](../1.2_Python_Basics/) |

---

**Master Linux fundamentals! 🐧**

*Thành thạo nền tảng Linux!*

</div>
