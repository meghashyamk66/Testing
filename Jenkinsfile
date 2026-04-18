pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/meghashyamk66/Testing.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("flaskapp:latest")
                }
            }
        }
        stage('Run Container') {
            steps {
                script {
                    // Stop old container if running
                    sh 'docker rm -f flaskapp || true'
                    // Run new container
                    sh 'docker run -d -p 80:5000 --name flaskapp flaskapp:latest'
                }
            }
        }
    }
}
