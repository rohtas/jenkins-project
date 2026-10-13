pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Getting source code'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-lab:latest .'
            }
        }
    }
}