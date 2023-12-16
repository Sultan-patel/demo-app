pipeline {
    agent any

    environment {
        DOCKER_HUB_CREDENTIALS = credentials('Dockerhub')
        DOCKER_REPO = 'badshahdocker/test'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', userRemoteConfigs: [[url: 'https://github.com/Sultan-patel/demo-app.git']]])
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.withRegistry('', DOCKER_HUB_CREDENTIALS) {
                        def customImage = docker.build("${DOCKER_REPO}:${BUILD_NUMBER}")
                        customImage.push()
                    }
                }
            }
        }
    }
}
