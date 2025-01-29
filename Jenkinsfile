pipeline {
agent any
tools{ jdk 'OpenJDK' }
environment {

JAVA_HOME = '/usr/lib/jvm/java-17-openjdk-amd64/'
DOCKER_TAG = getVersion()

}
stages {
stage ('Clone Stage') {
    steps {
        git'https://github.com/SamiraChallouf4123/SamiraChallouf.git'
    }
}
stage ('Docker Build') {
    steps {
        sh 'docker build -t samirachallouf4/Aston_Villa:${DOCKER_TAG} .'
    }
}
}
}
def getVersion() {
    return sh(returnStdout: true, script: 'git rev-parse --short HEAD').trim()
}