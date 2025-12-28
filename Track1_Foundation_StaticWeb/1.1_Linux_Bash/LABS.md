# Labs - Linux & Bash

## Lab 1: Điều hướng File System

**Mục tiêu:** Làm quen với các lệnh điều hướng cơ bản

### Bước 1: Kiểm tra vị trí hiện tại

```bash
pwd
```

### Bước 2: Liệt kê files

```bash
ls -la
```

### Bước 3: Di chuyển đến thư mục /tmp

```bash
cd /tmp
pwd
```

---

## Lab 2: Thao tác Files và Directories

**Mục tiêu:** Tạo, sao chép, di chuyển và xóa files

### Bước 1: Tạo cấu trúc thư mục

```bash
mkdir -p devops-lab/project1
cd devops-lab
```

### Bước 2: Tạo files

```bash
touch README.md
echo "Hello DevOps" > hello.txt
```

---

## Lab 3: Viết Bash Script đầu tiên

**Mục tiêu:** Tạo script tự động hóa

### Bước 1: Tạo file script

```bash
touch myscript.sh
chmod +x myscript.sh
```

### Bước 2: Viết nội dung

```bash
#!/bin/bash
echo "Welcome to DevOps Journey!"
date
```

### Bước 3: Chạy script

```bash
./myscript.sh
```
