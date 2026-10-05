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
	stage('Docker push') {
	    steps {
		withCredentials([
		    usernamePassword(
			credentialsId: 'dockerhub-devboard',
			usernameVariable: 'DOCKER_USERNAME',
			passwordVariable: 'DOCKER_PASSWORD'
		   )
			
		])
		{
                  sh '''
			echo "$DOCKER_PASSWORD" | docker login \
			-u "$DOCKER_USERNAME" \
			--password-stdin

			docker push kevaldevganiya2005/devboard-backend:latest
			docker push kevaldevganiya2005/devboard-frontend:latest

			docker logout
		     '''
		}
	   }
	}
    }
}
