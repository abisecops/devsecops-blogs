---
description: >-
  This is a simple steps to be followed to attach trivy report after docker
  build on jenkins pipeline to send on mail recipient.
cover: ../.gitbook/assets/image (116).png
coverY: 0
---

# Attach trivy report on email (jenkins pipeline)

### Steps to be followed

1. First trivy should be installed on the system:&#x20;

```bash
curl -sfL https://raw.githubusercontent.com/aquasecurity/trivy/master/contrib/install.sh | sh -s -- -b /usr/bin
```

2.  Follow the path:&#x20;

    [Dashboard](http://localhost:8080/) ->  [All](http://localhost:8080/view/all/) -> [Pipeline](https://localhost:8080)&#x20;
3. Pipeline script:&#x20;

```groovy
pipeline {
    agent any
    
    stages {
        stage('Download trivy-redis report') {
            steps {
                sh 'trivy image redis > trivy_redis.txt'
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: 'trivy_redis.txt', onlyIfSuccessful: true
            
                emailext attachLog: true, attachmentsPattern: 'trivy_redis.txt',
                body: "Trivy for redis has scanned.Please stay tuned for updates. More info at: ${env.BUILD_URL}",
                to: "abishek.kafle@hicare.in",
                subject: "Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}"
        }
    }
}
```

<figure><img src="../.gitbook/assets/image (116).png" alt=""><figcaption></figcaption></figure>

Now, we can download build log and trivy reports from email. :tada:
