pipeline {
    agent any


    stages {
        stage('Checkout') {
            steps {
                script {
                    // Checkout the code from the repository
                    checkout scm "https://github.com/Sultan-patel/demo-app.git"
                }
            }
        }
    }
}