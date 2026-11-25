pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t beginner-devops-website:latest .'
            }
        }

        stage('Deploy Application') {
            steps {
                sh '''
                    docker rm -f my-website || true

                    docker run -d \
                    --name my-website \
                    --restart unless-stopped \
                    -p 8081:80 \
                    beginner-devops-website:latest
                '''
            }
        }
    }
}
