---
icon: lucide/settings
tags:
  - Configuration
---

# Ansible Configuration

# Precedence Order

1. Command-line options
2. Environment variables
3. `ansible.cfg`
4. Defaults

#Config File Locations

1. `ANSIBLE_CONFIG`
2. `./ansible.cfg`
3. `~/.ansible.cfg`
4. `/etc/ansible/ansible.cfg`

!!! tip
Always create a project-level `ansible.cfg`.

# Disable Host Key Checking

```ini
[defaults]
host_key_checking = False
```
