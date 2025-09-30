pipeline {
    agent any

    tools {
        maven 'Maven'   // Use the name you configured under "Manage Jenkins → Global Tool Configuration"
        jdk 'JDK17'      // Use the JDK you configured in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                // Pulls code from your repository
                git branch: 'master',
                    url: 'https://github.com/bhargavpr99-sudo/demo-webapp.git'
            }
        }

        stage('Build WAR') {
            steps {
                sh 'mvn clean package'
            }
        }
    }

    post {
        success {
            // Store the WAR file in Jenkins so you can download it
            archiveArtifacts artifacts: 'target/*.war', fingerprint: true
        }
    }
}
