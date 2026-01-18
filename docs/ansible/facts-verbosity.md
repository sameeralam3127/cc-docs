---
icon: lucide/info
tags:
  - Facts
  - Debugging
---

# Facts and Verbosity

#Gathering Facts

```bash
ansible all -m setup
ansible all -m setup -a "filter=ansible_python_version"
```

# Verbose Levels

- `-v` basic
- `-vv` detailed
- `-vvv` debug (SSH, modules, facts)
