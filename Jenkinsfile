pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t mlops-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                docker stop mlops-container || true
                docker rm mlops-container || true
                docker run -d -p 5000:5000 --name mlops-container mlops-app
                '''
            }
        }
    }
}