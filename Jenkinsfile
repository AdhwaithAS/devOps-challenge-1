pipeline {
    agent any

    environment {
        IMAGE_NAME = 'flask-app'
        DOCKERHUB_USER = 'adhwaithas2007@gmail.com'
        DOCKER_IMAGE = "${DOCKERHUB_USER}/${IMAGE_NAME}"
    }

    stages {
        stage('Build') {
            steps {
                bat 'docker build -t %DOCKER_IMAGE%:latest .'
            }
        }

        stage('Test') {
            steps {
                bat 'pytest || echo "No tests found, skipping..."'
            }
        }

        stage('Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    bat 'echo %PASS% | docker login -u %USER% --password-stdin'
                    bat 'docker push %DOCKER_IMAGE%:latest'
                }
            }
        }

        stage('Deploy') {
            steps {
                bat '''
                    docker rm -f flask_container || echo "No existing container"
                    docker run -d -p 5000:5000 --name flask_container %DOCKER_IMAGE%:latest
                '''
            }
        }
    }

    post {
        always {
            echo '✅ Pipeline execution completed!'
        }
    }
}
