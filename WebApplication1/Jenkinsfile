pipeline {
    agent any
    environment {
        IMAGE_NAME = "umer23672@gmail.com/WebApplication1:latest"
    }
    stages {
        stage('Checkout Code') {
            steps {
                // Clone the repository from GitHub
                git branch: 'main', url: 'https://github.com/UmerMalik298/UmerAssign3.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                // Build the Docker image
                script {
                    docker.build("$webapplication1:latest}")
                }
            }
        }
        stage('Run Application') {
            steps {
                // Run the application using Docker
                script {
                    docker.image("${webapplication1:latest}").run('-d -p 8080:80')
                }
            }
        }
        stage('Clean Up') {
            steps {
                // Optional: Clean up old containers and images
                sh 'docker system prune -f'
            }
        }
    }
    post {
        always {
            echo 'Pipeline completed!'
        }
    }
}
