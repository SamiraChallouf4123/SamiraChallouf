def getVersion() {
    return sh(returnStdout: true, script: 'git rev-parse --short HEAD').trim()
}
environment {
    DOCKER_TAG = getVersion()
}
stage ('Docker Build') {
    steps {
        sh 'docker build -t jmlhmd/image_name:${DOCKER_TAG} .'
    }
}
