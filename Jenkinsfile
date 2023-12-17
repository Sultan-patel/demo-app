

pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', userRemoteConfigs: [[url: 'https://github.com/Sultan-patel/demo-app.git']]])
            }
        }
        stage("docker image build")
            steps {
                    sh ''' docker build -t test . '''
            }
    }
}

        