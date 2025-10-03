pipeline {
    agent { label 'server1' }

    tools {
    maven 'maven 3.9'  // MUST match exact name in Jenkins Tools
    }

    environment {
        GIT_REPO   = 'https://github.com/rehan0022/tech.git'
        GIT_BRANCH = 'main'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: "${GIT_BRANCH}", url: "${GIT_REPO}"
            }
        }

        stage('Build') {
            steps {
                echo 'Running Maven build...'
                sh 'mvn clean install -DskipTests'
            }
        }

        stage('Test') {
            steps {
                echo 'Running Maven tests...'
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging application...'
                sh 'mvn package'
            }
        }
    }

    post {
        success { echo '✅ Pipeline completed successfully!' }
        failure { echo '❌ Pipeline failed. Please check the logs.' }
    }
}
