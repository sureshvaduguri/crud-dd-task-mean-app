pipeline {
    agent any

    environment {
        BACKEND_IMAGE = "chandrasuresh/backend"
        FRONTEND_IMAGE = "chandrasuresh/frontend"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/sureshvaduguri/crud-dd-task-mean-app.git'
            }
        }

        stage('Build Backend Image') {
            steps {
                dir('backend') {
                    sh "docker build -t $BACKEND_IMAGE:latest ."
                }
            }
        }

        stage('Build Frontend Image') {
            steps {
                dir('frontend') {
                    sh "docker build -t $FRONTEND_IMAGE:latest ."
                }
            }
        }

        stage('Deploy Application') {
            steps {
                sh "docker-compose down"
                sh "docker-compose up -d"
            }
        }
    }
}
