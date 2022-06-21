pipeline {
    agent {
    // Equivalent to "docker build -f Dockerfile.build --build-arg version=1.0.2 ./build/
    dockerfile {
        filename 'Dockerfile.build'
        dir 'build'
        additionalBuildArgs  '--build-arg version=1.0.2'
        args '-v /tmp:/tmp'
    }
}
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

                    
