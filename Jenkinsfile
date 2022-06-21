pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh 'npm install'
                archiveArtifacts artifacts: './nodejs-demo-app.zip'
            }
        }
        stage ('Build Docker Image ') {
            when {
                branch 'main'
            }
            steps{
                script {
                    app =docker.build("tarasleto96/node-js-app")
                    app.inside {
                        sh 'echo $(curl localhost:8080)'
                    }
                }
            }
        }
        stage ('Push Docker Image') {
            when {
                branch 'main' 
            }
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker_hub_login'){
                        app.push ("${env.BUILD_NUMBER}")
                        app.push("latest")
                    }
                }
            }
        }
    }
}

                    
