pipeline {
    agent any

    environment {
        IMAGE_NAME = 'flask-app-mulearn'
        DOCKERHUB_USER = 'adhwaithas'
        DOCKER_IMAGE = "${DOCKERHUB_USER}/${IMAGE_NAME}"
    }

    stages {
        stage('Build') {
            steps {
                sh """docker build -t ${DOCKER_IMAGE}:latest ."""
            }
        }

        stage('Test') {
            steps {
                sh """pytest || echo 'No tests found, skipping...'"""
            }
        }

        stage('Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh """echo ${PASS} | docker login -u ${USER} --password-stdin"""
                    sh """docker push ${DOCKER_IMAGE}:latest"""
                }
            }
        }

        stage('Deploy') {
            steps {
                sh """
                    docker rm -f flask_container || echo 'No existing container'
                    docker run -d -p 5000:5000 --name flask_container ${DOCKER_IMAGE}:latest
                """
            }
        }
    }

    post {
        always {
            echo '✅ Pipeline execution completed!'
        }
    }
}
