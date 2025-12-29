# 🔧 Module 3.4: Configuration Management - Ansible

[![Duration](https://img.shields.io/badge/Duration-1%20week-blue?style=flat-square)](.)
[![Level](https://img.shields.io/badge/Level-Intermediate-orange?style=flat-square)](.)

> **Infrastructure as Code** - Automate with Ansible.
>
> *Infrastructure as Code - Tự động hóa với Ansible.*

---

## 🎯 Learning Objectives (Mục tiêu học tập)

After this module, you will (Sau module này, bạn sẽ):

- ✅ Understand Ansible architecture (Hiểu kiến trúc Ansible)
- ✅ Write Playbooks and roles (Viết Playbooks và roles)
- ✅ Manage inventory (Quản lý inventory)
- ✅ Use variables and templates (Sử dụng biến và templates)
- ✅ Explore Ansible Galaxy (Khám phá Ansible Galaxy)
- ✅ Work with AWX/Tower (Làm việc với AWX/Tower)

---

## 📚 Content (Nội dung)

### 1. Inventory

```ini
# inventory.ini
[webservers]
web1.example.com
web2.example.com

[databases]
db1.example.com

[all:vars]
ansible_user=ubuntu
```

### 2. Playbook

```yaml
# playbook.yml
---
- name: Configure web servers
  hosts: webservers
  become: yes
  
  tasks:
    - name: Install nginx (Cài nginx)
      apt:
        name: nginx
        state: present
        update_cache: yes
    
    - name: Start nginx (Khởi động nginx)
      service:
        name: nginx
        state: started
        enabled: yes
    
    - name: Copy config (Sao chép cấu hình)
      template:
        src: nginx.conf.j2
        dest: /etc/nginx/nginx.conf
      notify: Restart nginx
  
  handlers:
    - name: Restart nginx (Khởi động lại nginx)
      service:
        name: nginx
        state: restarted
```

### 3. Roles (Cấu trúc roles)

```
roles/
└── webserver/
    ├── tasks/
    │   └── main.yml
    ├── handlers/
    │   └── main.yml
    ├── templates/
    │   └── nginx.conf.j2
    ├── vars/
    │   └── main.yml
    └── defaults/
        └── main.yml
```

### 4. Common Commands (Các lệnh phổ biến)

```bash
# Run playbook (Chạy playbook)
ansible-playbook -i inventory.ini playbook.yml

# Check mode - dry run (Chế độ kiểm tra)
ansible-playbook playbook.yml --check

# Limit to specific hosts (Giới hạn hosts)
ansible-playbook playbook.yml --limit webservers

# Pass extra variables (Truyền biến)
ansible-playbook playbook.yml -e "env=production"
```

---

## 📝 Module Files (Các file trong Module)

| File | Description (Mô tả) |
|------|---------------------|
| [LABS.md](./LABS.md) | Hands-on labs (Bài thực hành) |
| [QUIZ.md](./QUIZ.md) | Knowledge check (Kiểm tra kiến thức) |
| [EXERCISES.md](./EXERCISES.md) | Exercises (Bài tập) |
| [SOLUTIONS.md](./SOLUTIONS.md) | Solutions (Đáp án) |

---

<div align="center">

### 🔗 Module Navigation (Điều hướng Module)

| ← Previous (Trước) | Current (Hiện tại) | Next (Tiếp) → |
|:------------------:|:------------------:|:-------------:|
| [3.3 Databases](../3.3_Databases_for_DevOps/) | **3.4 Ansible** | [3.5 Terraform](../3.5_Terraform_IaC/) |

---

**Master configuration management! 🔧**

*Thành thạo quản lý cấu hình!*

</div>
