pipeline {
    agent any
    environment {
        WEB_DIR = "/var/www/html"
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Deploy') {
            steps {
                sh '''
                rsync -av --delete --exclude .git * ${WEB_DIR}/
                '''
            }
        }
    }
    post {
        success {
            echo "✅ Deployment successful"
        }
        failure {
            echo "❌ Deployment failed"
        }
    }
}
