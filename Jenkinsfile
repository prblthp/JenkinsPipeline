pipeline {
  environment {
    repo = "prblthp/dockerpipeline
    DOCKERHUB_CREDENTIALS=credentials('dockerhubAccess')
 }
  agent any
  stages {
    stage('Docker Build') {
      steps {
        sh 'docker build -t $repo:v$BUILD_NUMBER .'
      }
    }
    stage('Docker Push') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
 
          
          sh 'docker push $repo:v$BUILD_NUMBER'
        }
      }
    
    stage('Clean docker image') {
      steps {
        sh 'docker rmi $repo:v$BUILD_NUMBER'
      }
    }
  }
}
