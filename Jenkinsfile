pipeline {
    environment {
        registryUrl = 'https://registry.hub.docker.com'
        dockerImage = ''
        imageName = 'melioratech/static-web'
        imageTag = 'latest'
    }
    agent any
    stages {
        stage('Build Image') {
            steps {
                dockerImage = docker.build  imageName + ":" + imageTag
            }
        }

        stage('Push image') {
            steps {
                withDockerRegistry([credentialsId: 'docker-hub', url: registryUrl]) {
                    dockerImage.push()
                }                              
            }
        }
    }
}