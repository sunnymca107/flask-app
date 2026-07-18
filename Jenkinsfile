pipeline{
    agent any 
    stages{
        stage('Build docker image')
        {
            steps{
                sh 'docker build -t sunnymca107/flask-app:v1 .'
                
            }
        }
        stage('dockerhub login')
        {
            steps{
                sh '''
                echo "sunnymca107" | docker login -u sunnymca107 --password-sunny@123
                '''
            }
        }

        stage('pushing image to dockerhub')
        {
            steps{
                sh 'docker push sunnymca107/flask-app:v1'
            }
            
        }

    }
}
