pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'github-credentials')]) {
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
                withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials')]) {
                    sh 'docker push your_username/your_image_name'
                }
            }
        }
    }
}
