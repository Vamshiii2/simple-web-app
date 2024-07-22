pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "vamshi0007gangamma/simple-web-app"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Vamshiii2/simple-web-app.git'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build(DOCKER_IMAGE)
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'vamshi0007gangamma') {
                        docker.image(DOCKER_IMAGE).push('latest')
                    }
                }
            }
        }
        
        stage('Deploy') {
            steps {
                // Deploy steps (e.g., Kubernetes, Docker Compose) can be added here
                echo 'Deploy stage - To be implemented'
            }
        }
    }
    
    post {
        success {
            echo 'Build succeeded'
        }
        failure {
            echo 'Build failed'
        }
    }
}