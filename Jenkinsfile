def registry = 'https://hub.docker.com/'
def imageName = 'https://hub.docker.com/repositories/badshahdocker/image'
pipeline {
    agent any

    stages {
        stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', userRemoteConfigs: [[url: 'https://github.com/Sultan-patel/demo-app.git']]])
            }
        }

    }
    stage(" Docker Build ") {
            steps {
                script {
                echo '<--------------- Docker Build Started --------------->'
                app = docker.build($imageName)
                echo '<--------------- Docker Build Ends --------------->'
                }
            }    }
    }
}    