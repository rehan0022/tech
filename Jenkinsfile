pipeline {
    agent { label 'server1' }   // or 'any' if no specific agent

    parameters {
        string(name: 'GIT_REPO', defaultValue: 'https://github.com/rehan0022/tech.git', description: 'Git repository URL')
        string(name: 'GIT_BRANCH', defaultValue: 'main', description: 'Branch to build')
    }

    environment {
        REPO   = "${params.GIT_REPO}"
        BRANCH = "${params.GIT_BRANCH}"
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Cloning ${REPO} (branch: ${BRANCH})"
                git branch: "${BRANCH}", url: "${REPO}"
            }
        }

        stage('Build') {
            steps {
                echo '⚙️ Running build steps...'
                // Example: Maven build
                // sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                echo '🧪 Running tests...'
                // Example: run unit tests
                // sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                echo '📦 Packaging artifacts...'
                // Example: create jar/war
                // archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }

        stage('Deploy') {
            steps {
                echo '🚀 Deploy stage (placeholder)'
                // Add deployment commands here
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline completed successfully!'
        }
        failure {
            echo '❌ Pipeline fa

