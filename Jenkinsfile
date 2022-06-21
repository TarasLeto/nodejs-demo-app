pipeline {
agent any
stages {

stage("build") {
steps {

sh """
docker build -t image_name .
"""

}
}
stage("run") {
steps {
 sh """
 docker run —publish 8012:8080 —rm image_name
"""

}

}
}

}
