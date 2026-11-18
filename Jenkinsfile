
pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'docker compose build'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker compose up -d'
            }
        }

        stage('Verify') {
            steps {
                sh 'docker compose ps'
                sh 'curl -f http://127.0.0.1:3333/'
            }
        }
    }

    post {
        success {
            echo 'KhmerHistory deployed successfully!'
        }

        failure {
            echo 'Deployment failed!'
        }
    }
}
