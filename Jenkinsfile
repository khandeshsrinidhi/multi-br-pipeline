pipeline {
    agent any
    environment {
    dockerhub = credentials('docker-hub1')
    }
    stages{
        stage('Docker Build') {
            steps {
                sh 'docker build -t srinidhi3108/ecomm1 .'
             }
          }
        stage('Docker Login') {
            steps {
                sh 'echo $dockerhub_PSW | docker login -u $dockerhub_USR --password-stdin'
            }
          }
        stage('Docker Push') {
            steps {
                sh 'docker push srinidhi3108/ecomm1'
            }
          }
        stage('Remove old images') {
            steps {
                sh 'docker rmi -f srinidhi3108/ecomm1'
              }
          }
        stage('Docker run'){
            steps{
                sh 'docker container run -dt --name ecomm-app --restart always -p 80:80 srinidhi3108/ecomm1'
            }
         }
     }
}
