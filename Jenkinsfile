pipeline {
    agent any
    tools {
        // Specify the correct Git tool installation name
        git 'Git'    }
    
    environment {
        DOCKER_HUB_CREDENTIALS = credentials('Dockerhub')
        DOCKER_REPO = 'badshahdocker/test'
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Checkout the code from the repository
                    checkout([$class: 'GitSCM', userRemoteConfigs: [[url: 'https://github.com/Sultan-patel/demo-app.git']]])
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build Docker image and push to Docker Hub
                    docker.withRegistry('', DOCKER_HUB_CREDENTIALS) {
                        def customImage = docker.build("${DOCKER_REPO}:${BUILD_NUMBER}")
                        customImage.push()
                    }
                }
            }
        }
    }
}
