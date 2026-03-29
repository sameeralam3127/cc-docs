---
icon: lucide/settings
tags:
  - Configuration
  - Database
---

# SonarQube Configuration

---

## Configure Database Connection

Edit the configuration file:

```bash
sudo nano /opt/sonarqube/conf/sonar.properties
```

Add/replace these lines:

```properties
sonar.jdbc.username=sonar
sonar.jdbc.password=sonar
sonar.jdbc.url=jdbc:postgresql://localhost:5432/sonar
```

---

## Start SonarQube

```bash
cd /opt/sonarqube/bin/linux-x86-64
sudo -u sonar ./sonar.sh start
```

Check status:

```bash
sudo -u sonar ./sonar.sh status
```

Access SonarQube at: **http://your-server-ip:9000**

Default credentials:

- **Username**: `admin`
- **Password**: `admin`

---

**Tip**: For production, set up as a systemd service.

**Official Guide**: [Install the Server](https://docs.sonarsource.com/sonarqube/latest/setup-and-upgrade/install-the-server/)
