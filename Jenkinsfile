pipeline {
  agent any
  stages {
    stage('Build') {
       steps {
         nodejs('Node-10.17')
            sh 'npm install'
            sh ' npm buid'
         
       }
    }
    stage('Test') {
      steps {
        sh 'npm test'
      }
    }
  }
}
