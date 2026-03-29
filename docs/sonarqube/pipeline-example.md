---
icon: lucide/code
tags:
  - Pipeline
  - Groovy
---

# Jenkins Pipeline with SonarQube Analysis

---

## Example Pipeline (Declarative)

```groovy
pipeline {
    agent any

    environment {
        SONAR_TOKEN = credentials('sonar-token')  // Add your token in Jenkins Credentials
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/your-repo.git'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {  // Name must match Jenkins config
                    sh '''
                        sonar-scanner \
                          -Dsonar.projectKey=your-project-key \
                          -Dsonar.sources=. \
                          -Dsonar.host.url=http://your-sonarqube:9000 \
                          -Dsonar.token=$SONAR_TOKEN
                    '''
                }
            }
        }

        stage('Quality Gate') {
            steps {
                timeout(time: 10, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'   // or your build command
            }
        }
    }
}
```

---

## How to Use

1. Create a new **Pipeline** job in Jenkins
2. Paste the script or use `Jenkinsfile` from repository
3. Add `sonar-token` as Secret Text credential in Jenkins

**Tip**: Use `waitForQualityGate` to fail the build if quality standards are not met.
