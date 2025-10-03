pipeline {
    agent { label 'server1' }

    // Use the exact Maven tool name configured in Jenkins
    tools {
        maven 'maven 3.9.11'
    }

    environment {
        GIT_REPO   = 'https://github.com/rehan0022/tech.git'
        GIT_BRANCH = 'main'
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Cloning repository ${GIT_REPO} (branch: ${GIT_BRANCH})"
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
        success {
            echo '✅ Pipeline completed successfully!'
        }
        failure {
            echo '❌ Pipeline failed. Check the console logs for details.'
        }
    }
}
