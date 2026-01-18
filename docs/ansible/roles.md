---
icon: lucide/folders
tags:
  - Roles
---

# Roles

# Create Role

```bash
ansible-galaxy role init my_role
```

# Role Structure

tasks/
handlers/
templates/
files/
vars/
defaults/
meta/

# Using a Role

```yaml
- hosts: webservers
  roles:
    - my_role
```
