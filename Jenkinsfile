pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/aliaminsalah/simple-web-app.git'
            }
        }
        
        stage('Build & Test') {
            steps {
                script {
                    sh 'docker-compose down || true' 
                    sh 'docker-compose up --build -d'
                   
                    sh 'sleep 10' 
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
