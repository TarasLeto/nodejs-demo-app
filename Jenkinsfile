pipeline {
agent any
stages {
stage("build") {
steps {

sh """
docker build -t nodejs-app .
"""

}
}
stage("run") {
steps {
 sh """
 docker run --publish 8012:8080 --rm nodejs-app
"""

}

}
}

}
