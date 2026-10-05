pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Backend Test') {
            steps {
                sh '''
                    cd backend
                    go test ./...
                '''
            }
        }

        stage('Frontend Build') {
            steps {
                sh '''
                    cd frontend
                    npm ci --legacy-peer-deps
                    npm run build
                '''
            }
        }

        stage('Docker Build') {
            steps {
                sh '''
                    docker build \
                      -t kevaldevganiya2005/devboard-backend:latest \
                      ./backend

                    docker build \
                      -t kevaldevganiya2005/devboard-frontend:latest \
                      ./frontend
                '''
            }
        }

        stage('Docker Images Check') {
            steps {
                sh '''
                    docker images | grep devboard
                '''
            }
        }
    }
}
