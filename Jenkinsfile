pipeline {
    agent any

    environment {
        DOCKER_COMPOSE_VERSION = '2.1.1' 
    }

    stages {
        stage('Check docker-compose') {
            steps {
                script {
                    sh 'docker-compose --version'
                }
            }
        }
        
        stage('Checkout') {
            steps {
                git 'https://github.com/aliaminsalah/simple-web-app.git'
            }
        }
        
        stage('Build & Test') {
            steps {
                script {
                    
                    sh 'docker-compose down'
                    sh 'docker-compose up --build -d'
                }
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                
            }
        }
    }

    post {
        always {
            echo 'Shutting down any running containers...'
            sh 'docker-compose down'
        }
    }
}
