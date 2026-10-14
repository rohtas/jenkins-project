pipeline {
    agent any

    stages {

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh 'sonar-scanner'
                }
            }
        }

        stage('Build Docker Image') {
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