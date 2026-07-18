pipeline {
    agent any
    environment {
        IMAGE="sunnymca107/flask-app:${BUILD_NUMBER}"
    }
    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/sunnymca107/flask-app.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'pip3 install -r requirements.txt'
            }
        }
        stage('Docker Build') {
            steps {
                sh 'docker build -t $IMAGE .'
            }
        }
        stage('Docker Push') {
            steps {
                sh 'docker push $IMAGE'
            }
        }
        stage('Deploy Docker Swarm') {
            steps {
                sh '''
                docker service rm flask-app || true
                docker service create \
                --name flask-app \
                -p 5000:5000 \
                $IMAGE
                '''
            }
        }
    }
}
