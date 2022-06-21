pipeline {
agent any
stages {
stage("build") {
steps {

sh """
sudo docker build -t nodejs-app .
"""

}
}
stage("run") {
steps {
 sh """
 sudo docker run --publish 8012:8080 --rm nodejs-app
"""

}

}
}

}
