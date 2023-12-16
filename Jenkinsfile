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
    }
}    