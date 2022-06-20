pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh './gradlew build --no-daemon'
                archiveArtifacts artifacts: 'dist/nodejs-demo-app.zip'
            }
        }
        stage ('Build Docker Image ') {
            when {
                branch 'master'
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
                brach 'master' 
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

                    
