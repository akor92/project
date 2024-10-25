pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'github-creds')]) {
                    git branch: 'main', url: 'https://github.com/akor92/project.git' 
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t akor92/portfolio .'
            }
        }

        stage('Push Docker Image to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds')]) {
                    sh 'docker push akor92/portfolio'
                }
            }
        }
    }
}
