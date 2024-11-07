pipeline {
    agent any

    environment {
        DOCKER_COMPOSE_VERSION = '1.29.2' // تأكد من تغيير الإصدار إذا لزم الأمر
    }

    stages {
        stage('Check docker-compose') {
            steps {
                script {
                    // تحقق من أن docker-compose مثبت
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
                    // بناء وتشغيل التطبيق باستخدام docker-compose
                    sh 'docker-compose down'
                    sh 'docker-compose up --build -d'
                }
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                // هنا يمكنك إضافة خطوة نشر التطبيق إذا لزم الأمر
            }
        }
    }

    post {
        always {
            // إيقاف الحاويات بعد تنفيذ أي مرحلة
            echo 'Shutting down any running containers...'
            sh 'docker-compose down'
        }
    }
}
