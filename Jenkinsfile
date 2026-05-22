pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/AnandhuLatheesh/jenkins-ci-cd-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'sudo docker build -t mlops-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                sudo docker stop mlops-container || true
                sudo docker rm mlops-container || true
                sudo docker run -d -p 5000:5000 --name mlops-container mlops-app
                '''
            }
        }
    }
}