---
icon: lucide/plug
tags:
  - Jenkins
  - Integration
---

# SonarQube Integration with Jenkins

---

## Step 1: Install SonarQube Scanner Plugin

1. Go to Jenkins → **Manage Jenkins** → **Manage Plugins**
2. Search for **"SonarQube Scanner"** in the Available tab
3. Install and restart Jenkins

---

## Step 2: Configure SonarQube Server in Jenkins

1. **Manage Jenkins** → **Configure System**
2. Scroll to **SonarQube servers** section
3. Click **Add SonarQube**
   - **Name**: `SonarQube`
   - **Server URL**: `http://your-sonarqube-server:9000`
   - **Server Authentication Token**: (Generate from SonarQube → My Account → Security)

---

**Next**: [Pipeline Example →](./pipeline-example.md)

**Official Jenkins Integration**: [SonarQube Jenkins Docs](https://docs.sonarsource.com/sonarqube/latest/analyzing-source-code/ci-integration/jenkins-integration/)
