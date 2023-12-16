pipeline {
    agent any

    tools {
        git 'Default'
    }

    environment {
        DOCKER_REPO = 'badshahdocker/test'
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    checkout([$class: 'GitSCM', userRemoteConfigs: [[url: 'https://github.com/Sultan-patel/demo-app.git']]])
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    withCredentials([string(credentialsId: 'Dockerhub', variable: 'DOCKER_HUB_CREDENTIALS_USR')]) {
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
