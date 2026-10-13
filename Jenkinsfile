pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-lab:latest .'
            }
        }

        stage('Remove Old Container') {
            steps {
                sh 'docker rm -f website || true'
            }
        }

        stage('Deploy Website') {
            steps {
                sh 'docker run -d --name website -p 8082:80 jenkins-lab:latest'
            }
        }

        stage('Verification') {
            steps {
                sh 'docker ps'
            }
        }
    }
}