pipeline {
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
  }
}
