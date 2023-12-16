def registry = 'https://hub.docker.com/'
def imageName = 'badshahdocker/image'  // Removed unnecessary 'https://hub.docker.com/repositories/'

pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', userRemoteConfigs: [[url: 'https://github.com/Sultan-patel/demo-app.git']]])
            }
        }

        stage('Docker Build') {
            steps {
                script {
                    echo '<--------------- Docker Build Started --------------->'
                    app = docker.build(imageName)  // Used 'imageName' instead of '$imageName'
                    echo '<--------------- Docker Build Ends --------------->'
                }
            }
        }
    }
}
