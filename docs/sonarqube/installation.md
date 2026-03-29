---
icon: lucide/download
tags:
  - Installation
  - Ubuntu
---

# SonarQube Installation on Ubuntu

This guide walks you through installing SonarQube on Ubuntu using PostgreSQL.

---

## Prerequisites

- Ubuntu 20.04 / 22.04 / 24.04
- At least 4 GB RAM (8 GB recommended)
- Java 17

```bash
sudo apt update
sudo apt install openjdk-17-jdk -y
java -version
```

---

## Step 1: Install PostgreSQL

```bash
sudo apt install postgresql postgresql-contrib -y
```

Create database and user:

```bash
sudo -u postgres psql
```

```sql
CREATE USER sonar WITH PASSWORD 'sonar';
CREATE DATABASE sonar OWNER sonar;
GRANT ALL PRIVILEGES ON DATABASE sonar TO sonar;
\q
```

---

## Step 2: Download and Install SonarQube

Download the latest version from the [official downloads page](https://www.sonarsource.com/products/sonarqube/downloads/).

```bash
# Example for latest version (replace with current link)
wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-2026.1.2.zip

sudo apt install unzip -y
unzip sonarqube-*.zip
sudo mv sonarqube-* /opt/sonarqube
```

---

## Step 3: Create Dedicated User (Recommended)

```bash
sudo useradd -r -m -U -d /opt/sonarqube -s /bin/false sonar
sudo chown -R sonar:sonar /opt/sonarqube
```
