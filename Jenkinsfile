pipeline {
    agent {
  label 'server1'
}
// this is agent

    environment {
        GIT_REPO = 'https://github.com/rehan0022/tech.git'
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
                echo 'Running build steps (if any)'
                // Add your build commands here, e.g., shell scripts, Maven, npm, etc.
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests (if any)'
                // Add your test commands here
            }
        }

        stage('Post Actions') {
            steps {
                echo 'Post-build actions can go here'
                // Optional: commit & push changes if your pipeline modifies files
                // sh 'git config user.name "rehan0022"'
                // sh 'git config user.email "rehan.sk0022@gmail.com"'
                // sh 'git add .'
                // sh 'git commit -m "Automated commit from Jenkins" || echo "No changes"'
                // sh 'git push origin main'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
