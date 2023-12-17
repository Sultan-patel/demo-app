pipeline {
    agent any

    environment {
        DOCKER_IMAGE_NAME = "badshahdocker/nodejs-app"
        DOCKER_IMAGE_TAG = "latest"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', userRemoteConfigs: [[url: 'https://github.com/Sultan-patel/demo-app.git']]])
            }
        }

        stage('Build and Push Docker Image') {
            steps {
                script {
        
                    sh "docker build -t ${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG}: ."
                    sh "docker login -u myregis  -p Sultan@12"
                    sh "docker push ${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG}"
                }
            }
        }
    }
    }

