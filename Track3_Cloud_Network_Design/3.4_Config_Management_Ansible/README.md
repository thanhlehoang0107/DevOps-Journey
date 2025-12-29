# 🔧 Module 3.4: Configuration Management - Ansible

> **Infrastructure as Code** - Automate với Ansible.

---

## 🎯 Learning Objectives

- ✅ Ansible architecture
- ✅ Playbooks và roles
- ✅ Inventory management
- ✅ Variables và templates
- ✅ Ansible Galaxy
- ✅ AWX/Tower

---

## 📚 Content

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
    - name: Install nginx
      apt:
        name: nginx
        state: present
        update_cache: yes
    
    - name: Start nginx
      service:
        name: nginx
        state: started
        enabled: yes
    
    - name: Copy config
      template:
        src: nginx.conf.j2
        dest: /etc/nginx/nginx.conf
      notify: Restart nginx
  
  handlers:
    - name: Restart nginx
      service:
        name: nginx
        state: restarted
```

### 3. Roles

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

### 4. Common Commands

```bash
# Run playbook
ansible-playbook -i inventory.ini playbook.yml

# Check mode (dry run)
ansible-playbook playbook.yml --check

# Limit to specific hosts
ansible-playbook playbook.yml --limit webservers

# Pass extra variables
ansible-playbook playbook.yml -e "env=production"
```

---

## 📝 Module Files

- [LABS.md](./LABS.md) | [QUIZ.md](./QUIZ.md) | [EXERCISES.md](./EXERCISES.md)
