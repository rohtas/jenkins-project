pipeline {
    agent any

    stages {

        stage('Build Image') {
            steps {
                sh 'docker build -t website:latest .'
            }
        }

        stage('Remove Old Container') {
            steps {
                sh 'docker rm -f website || true'
            }
        }

        stage('Deploy Website') {
            steps {
                sh 'docker run -d --name website -p 8082:80 website:latest'
            }
        }
    }
}