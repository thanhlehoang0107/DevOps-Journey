# 📝 Quiz - Linux & Bash

> **Knowledge Check for Linux and Bash Scripting**
>
> *Kiểm tra kiến thức về Linux và Bash scripting*

---

## Hướng dẫn

- **Tổng số câu hỏi**: 20 câu
- **Thời gian**: 15-20 phút
- **Đáp án**: Cuối trang

---

## Phần 1: Linux Basics (10 câu)

### Câu 1: Thư mục gốc

Trong Linux, thư mục gốc (root directory) được ký hiệu là gì?

- A) `~`
- B) `/`
- C) `\`
- D) `$`

---

### Câu 2: Home Directory

Lệnh nào đưa bạn về home directory của user hiện tại?

- A) `cd home`
- B) `cd /`
- C) `cd ~`
- D) `cd ..`

---

### Câu 3: Liệt kê files ẩn

Lệnh nào hiển thị tất cả files kể cả hidden files (bắt đầu bằng dấu chấm)?

- A) `ls -l`
- B) `ls -h`
- C) `ls -a`
- D) `ls -r`

---

### Câu 4: Tạo thư mục lồng nhau

Để tạo cấu trúc thư mục `parent/child/grandchild` khi các thư mục cha chưa tồn tại, dùng lệnh gì?

- A) `mkdir parent/child/grandchild`
- B) `mkdir -r parent/child/grandchild`
- C) `mkdir -p parent/child/grandchild`
- D) `mkdir --recursive parent/child/grandchild`

---

### Câu 5: Xem nội dung file

Lệnh nào hiển thị 10 dòng cuối cùng của một file?

- A) `head file.txt`
- B) `tail file.txt`
- C) `cat file.txt`
- D) `less file.txt`

---

### Câu 6: Tìm kiếm trong file

Lệnh nào tìm tất cả các dòng chứa từ "error" trong file log.txt, không phân biệt hoa thường?

- A) `grep error log.txt`
- B) `grep -i error log.txt`
- C) `find error log.txt`
- D) `search -i error log.txt`

---

### Câu 7: Permission Number

Permission `rwxr-xr--` tương đương với số nào?

- A) 644
- B) 755
- C) 754
- D) 777

---

### Câu 8: Thêm execute permission

Lệnh nào thêm quyền execute cho owner của file script.sh?

- A) `chmod +x script.sh`
- B) `chmod u+x script.sh`
- C) `chmod 755 script.sh`
- D) Tất cả đều đúng

---

### Câu 9: Process Management

Lệnh nào dừng (force kill) process có PID 1234?

- A) `kill 1234`
- B) `kill -9 1234`
- C) `stop 1234`
- D) `terminate 1234`

---

### Câu 10: Package Manager

Trên Ubuntu/Debian, lệnh nào cài đặt package nginx?

- A) `apt nginx install`
- B) `install apt nginx`
- C) `sudo apt install nginx`
- D) `sudo yum install nginx`

---

## Phần 2: Bash Scripting (10 câu)

### Câu 11: Shebang

Dòng đầu tiên của bash script nên là gì?

- A) `#/bin/bash`
- B) `#!/bin/bash`
- C) `//bin/bash`
- D) `@!/bin/bash`

---

### Câu 12: Biến trong Bash

Cách nào đúng để gán giá trị cho biến trong Bash?

- A) `NAME = "DevOps"`
- B) `NAME="DevOps"`
- C) `$NAME="DevOps"`
- D) `set NAME="DevOps"`

---

### Câu 13: Sử dụng biến

Để in giá trị của biến `NAME`, dùng cú pháp nào?

- A) `echo NAME`
- B) `echo $NAME`
- C) `echo %NAME%`
- D) `echo ${NAME}`
- E) B và D đều đúng

---

### Câu 14: So sánh số

Trong Bash, operator nào dùng để kiểm tra số A lớn hơn số B?

- A) `$A > $B`
- B) `$A -gt $B`
- C) `$A -greater $B`
- D) `$A == $B`

---

### Câu 15: Kiểm tra file tồn tại

Trong điều kiện if, flag nào kiểm tra file có tồn tại không?

- A) `[ -e file.txt ]`
- B) `[ -f file.txt ]`
- C) `[ -d file.txt ]`
- D) A và B đều đúng

---

### Câu 16: For Loop

Vòng lặp sau in ra gì?

```bash
for i in 1 2 3; do
    echo $i
done
```

- A) `1 2 3` (trên 1 dòng)
- B) `123`
- C) Mỗi số trên 1 dòng (1, 2, 3)
- D) Lỗi syntax

---

### Câu 17: Command Substitution

Cú pháp nào ĐÚNG để gán output của lệnh vào biến?

- A) `DATE=date`
- B) `DATE=$(date)`
- C) `DATE=${date}`
- D) `DATE=$[date]`

---

### Câu 18: Pipe

Lệnh `ps aux | grep nginx` làm gì?

- A) Liệt kê tất cả processes có tên nginx
- B) Chạy ps và grep đồng thời
- C) Lấy output của `ps aux` và tìm dòng chứa "nginx"
- D) Xóa process nginx

---

### Câu 19: Redirect Output

Lệnh `echo "Hello" >> file.txt` khác với `echo "Hello" > file.txt` như thế nào?

- A) Không khác gì
- B) `>>` append vào file, `>` overwrite file
- C) `>>` ghi vào stderr, `>` ghi vào stdout
- D) `>>` tạo file mới, `>` ghi đè

---

### Câu 20: Exit Code

Trong Bash, exit code nào thường báo hiệu command thực thi thành công?

- A) 1
- B) -1
- C) 0
- D) 255

---

## 📋 Đáp án

<details>
<summary>Click để xem đáp án</summary>

### Phần 1: Linux Basics

| Câu | Đáp án | Giải thích |
|-----|--------|------------|
| 1 | **B** | `/` là root directory trong Linux |
| 2 | **C** | `~` là shortcut cho home directory |
| 3 | **C** | `-a` (all) hiển thị cả hidden files |
| 4 | **C** | `-p` (parents) tạo thư mục cha nếu chưa có |
| 5 | **B** | `tail` hiển thị cuối file, mặc định 10 dòng |
| 6 | **B** | `-i` (ignore case) không phân biệt hoa thường |
| 7 | **C** | rwx=7, r-x=5, r--=4 → 754 |
| 8 | **D** | Cả 3 cách đều thêm execute permission |
| 9 | **B** | `-9` là signal SIGKILL (force) |
| 10 | **C** | Ubuntu/Debian dùng apt |

### Phần 2: Bash Scripting

| Câu | Đáp án | Giải thích |
|-----|--------|------------|
| 11 | **B** | `#!` (shebang) + đường dẫn interpreter |
| 12 | **B** | KHÔNG có dấu cách quanh `=` |
| 13 | **E** | `$NAME` và `${NAME}` đều hợp lệ |
| 14 | **B** | `-gt` (greater than) cho so sánh số |
| 15 | **D** | `-e` (exist) và `-f` (regular file) đều check tồn tại |
| 16 | **C** | `echo` mặc định xuống dòng sau mỗi lần |
| 17 | **B** | `$()` là command substitution |
| 18 | **C** | Pipe (`\|`) truyền output làm input |
| 19 | **B** | `>>` append, `>` overwrite |
| 20 | **C** | 0 = success, khác 0 = error |

### Điểm số

- **18-20 câu đúng**: Xuất sắc! ⭐⭐⭐
- **14-17 câu đúng**: Tốt! Tiếp tục ⭐⭐
- **10-13 câu đúng**: Cần ôn tập thêm ⭐
- **< 10 câu đúng**: Hãy đọc lại README.md

</details>

---

## 🔗 Navigation

[⬅️ LABS](./LABS.md) | [README](./README.md) | [EXERCISES ➡️](./EXERCISES.md)

---

*Cập nhật: 2025-12-29*
