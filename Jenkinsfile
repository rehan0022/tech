pipeline {
    agent { label 'server1' }

    tools {
        // Must match your Jenkins global tool name
        maven 'maven 3.9.11'
    }

    environment {
        GIT_REPO   = 'https://github.com/rehan0022/tech.git'
        GIT_BRANCH = 'main'
        MAVEN_OPTS = "-Dmaven.repo.local=$WORKSPACE/.m2/repository"
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
                echo '⚙️ Running Maven build (skip tests)...'
                sh 'mvn clean install -DskipTests'
            }
        }

        stage('Test') {
            steps {
                echo '🧪 Running tests...'
                // Use -DskipTests=false to force tests to run if you want them later
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                echo '📦 Packaging application...'
                sh 'mvn package -DskipTests'
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
