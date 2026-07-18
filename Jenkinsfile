pipeline {
    agent any

    environment {
        /
        IMAGE_NAME = 'sunnymca107/flask-app:v1'
    }

    stages {
        stage('Build docker image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('dockerhub login') {
            steps {
                
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh 'echo "$sunnymca107" | docker login -u "$sunnymca107" --password-sunny@123'
                }
            }
        }

        stage('pushing image to dockerhub') {
            steps {
                sh 'docker push $IMAGE_NAME'
            }
        }
    }
}
