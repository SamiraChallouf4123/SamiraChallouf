pipeline {
    agent any
    tools {
        jdk 'OpenJDK'
    }
    environment {
        JAVA_HOME = '/usr/lib/jvm/java-17-openjdk-amd64/'
        DOCKER_TAG = getVersion()
    }
    stages {
        stage('Clone Stage') {
            steps {
                git 'https://github.com/SamiraChallouf4123/SamiraChallouf.git'
            }
        }
        stage('Docker Build') {
            steps {
                sh 'docker build -t samirachallouf4/aston_villa:${DOCKER_TAG} .'
            }
        }
        stage('DockerHub Push') {
            steps {
                sh 'sudo docker login -u samirachallouf4 -p samira123'
                sh 'sudo docker push samirachallouf4/aston_villa:${DOCKER_TAG}'
            }
        }
        stage('Deploy') {
            steps {
                    sh "ssh root@172.16.130.155"
                    sh "ssh root@172.16.130.155 'sudo docker run ${aston_villa}:${DOCKER_TAG}'"
                }
            
        }
    }
}

def getVersion() {
    return sh(returnStdout: true, script: 'git rev-parse --short HEAD').trim()
}
