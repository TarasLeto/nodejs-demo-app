pipeline {
  environment {
    registry = "tarasleto96/repo-images-test"
    registryCredential = ‘docker_hub_login ’
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git '/https://github.com/TarasLeto/nodejs-demo-app'
      }
    }
    stage('Build') {
       steps {
         sh 'npm install'
       }
    }
    stage('Test') {
      steps {
        sh 'npm test'
      }
    }
    stage('Building image') {
      steps{
        script {
          docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
  stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $registry:$BUILD_NUMBER"
      }
    }
  }
}
