---
icon: lucide/folders
tags:
  - Roles
---

# Ansible Roles

Roles help you organize automation into reusable, predictable pieces. They are the right next step once a playbook starts getting large.

## Create a Role

```bash
ansible-galaxy role init my_role
```

## Typical Role Structure

```text
tasks/
handlers/
templates/
files/
vars/
defaults/
meta/
```

## Use a Role in a Playbook

```yaml
- hosts: webservers
  roles:
    - my_role
```

## When to Use Roles

Roles are useful when:

- The same tasks are reused across playbooks
- You want clearer structure for a team
- Variables, templates, and handlers belong together

## Quick Check

```bash
ansible-galaxy role init nginx_role
```
