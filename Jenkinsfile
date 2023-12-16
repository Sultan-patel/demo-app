pipeline {
    agent any

    tools {
        // Specify the correct Git tool installation name
        git 'Default'
    }

    environment {
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
                    // Use withCredentials to securely access Docker Hub credentials
                    withCredentials([string(credentialsId: 'Dockerhub', variable: 'DOCKER_HUB_CREDENTIALS_USR')]) {
                        // Build Docker image and push to Docker Hub
                        docker.withRegistry('', DOCKER_HUB_CREDENTIALS_USR) {
                            def customImage = docker.build("${DOCKER_REPO}:${BUILD_NUMBER}")
                            customImage.push()
                        }
                    }
                }
            }
        }
    }
}
