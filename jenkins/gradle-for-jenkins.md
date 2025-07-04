# Gradle for jenkins

{% embed url="https://sdkman.io/install" %}

```groovy
pipeline {
    agent any
    
    environment {
        MAINTAINER = "${MAINTAINER}"
        ANDROID_HOME = "/home/admin/.android/sdk" // Set the ANDROID_HOME environment variable
    }
    
    stages {
        stage('Notify Initial Deployment Notification') {
            steps {
                script {
                    def userId = currentBuild.rawBuild.getCause(hudson.model.Cause$UserIdCause).getUserId()

                    emailext attachLog: true,
                        mimeType: 'text/html',
                        subject: "Deployment Started: Gradle for apk",
                        to: "${MAINTAINER}",
                        body: "<p>The deployment process for Gradle has started by ${userId}.</p><p>Please stay tuned for updates: ${env.BUILD_URL} </p>"
                }
            }
        }

        stage('Git Pull') {
            steps {
                git branch: 'devops', credentialsId: 'ms-git-cred', url: 'https://github.com/support/hmobileapp-customerlatest.git'
                echo "Git Pull Success"
            }
        }

        stage('Build APK') {
            steps {
                sh 'chmod +x *'
                sh '''
                    # Set the sdk.dir property in local.properties
                    echo "sdk.dir=${ANDROID_HOME}" > local.properties

                    # Run Gradle build
                    ./gradlew clean assembleDebug
                    ./gradlew build
                '''
            }
        }

        stage('Send APK via Email') {
            steps {
                emailext body: 'APK file attached.', 
                    subject: 'APK Build Notification', 
                    to: "${MAINTAINER}", 
                    attachmentsPattern: '**/*.apk'
            }
        }
    }
}

```
