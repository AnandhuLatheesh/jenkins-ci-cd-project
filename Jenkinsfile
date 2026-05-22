pipeline
 {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-app .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker stop jenkins-container || true
                docker rm jenkins-container || true
                docker run -d -p 5000:5000 --name jenkins-container jenkins-app
                '''
            }
        }
    }
}