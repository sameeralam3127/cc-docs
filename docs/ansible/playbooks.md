---
icon: lucide/file-code
tags:
  - Playbooks
---

# Writing Your First Playbook

```yaml
---
- name: Install Apache on webservers
  hosts: webservers
  become: yes
  tasks:
    - name: Ensure Apache is installed
      apt:
        name: apache2
        state: present
      when: ansible_os_family == "Debian"
```

#Run Playbook

```bash
ansible-playbook -i hosts.ini playbook.yml
```
