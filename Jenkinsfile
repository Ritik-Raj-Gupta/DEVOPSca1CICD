pipeline {
    agent any

    environment {
        // Path to docker compose file
        COMPOSE_FILE = 'docker-compose.yml'
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Clone repository
                    checkout scm
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    echo 'Building Docker images...'
                    sh 'docker-compose build'
                }
            }
        }

        stage('Deploy') {
    steps {
        script {
            echo 'Stopping any existing containers...'
            sh 'docker-compose down -v --remove-orphans || true'
            
            echo 'Deploying application...'
            sh 'docker-compose up -d'
        }
    }
}
    }
}
