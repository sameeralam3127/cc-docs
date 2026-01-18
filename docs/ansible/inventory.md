---
icon: lucide/server
tags:
  - Inventory
---

# Working with Inventory

#Static Inventory Example

```ini
[webservers]
192.168.1.10
192.168.1.11

[databases]
db1.example.com
```

#List Hosts

```bash
ansible all --list-hosts
```

#Python Interpreter Override

```ini
[webservers]
192.168.1.10 ansible_python_interpreter=/usr/bin/python3
```
