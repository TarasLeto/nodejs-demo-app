pipeline {
  agent any
  stages {
    stage('Build') {
       steps {
         nodejs('Node-10.17')
         script {
            sh 'npm install'
            sh ' npm build package.json'
         }
       }
    }
    stage('Test') {
      steps {
        sh 'npm test'
      }
    }
  }
}
