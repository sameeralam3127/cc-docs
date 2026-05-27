---
icon: lucide/book-open
tags:
  - Ansible
  - Overview
---

# Ansible Automation Overview

Ansible is an automation tool for configuring servers, deploying applications, and running repeatable operational tasks. It is a good fit when you want simple, readable automation without installing agents on every Linux host.

## What Ansible Is Good For

- Provisioning packages and services
- Managing configuration files
- Running application deployments
- Standardizing repeated operational work

## Why Teams Like It

- Agentless for most Linux environments
- Uses SSH for remote access
- Stores automation in YAML playbooks
- Easy to read during reviews and troubleshooting

## Key Building Blocks

- **Inventory**: The list of hosts and groups you manage
- **Playbooks**: YAML files that define tasks
- **Modules**: Reusable units of work such as `apt`, `copy`, and `service`
- **Roles**: A structured way to organize reusable automation

## When to Use Ansible vs Terraform

Use Ansible when the main job is configuring systems or running tasks on existing machines.

Use Terraform when the main job is creating infrastructure such as VPCs, subnets, load balancers, or cloud instances.

Many teams use both:

- Terraform creates infrastructure
- Ansible configures what runs on it

## What Came Before Ansible

Before Ansible became common, teams often relied on:

- Shell scripts
- Python scripts
- Manual SSH sessions
- Agent-based tools such as Puppet and Chef

Ansible became popular because it reduced complexity while still supporting real production work.

## Quick Check

```bash
ansible --version
ansible all -m ping -i inventory.ini
```

## Next Steps

- Review [Ansible core concepts](basics.md)
- Practice with [Ansible interview questions](interview-questions.md)
