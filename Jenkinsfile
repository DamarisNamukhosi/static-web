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
                script {
                    docker.build  imageName + ":" + imageTag
                    dockerImage = docker.build  imageName + ":" + imageTag
                }
            }
        }

        stage('Push Image to Registry') {
            steps {
                script {
                    withDockerRegistry([credentialsId: 'docker-hub', url: registryUrl]) {
                    dockerImage.push()
                }  
                }                            
            }
        }
    }
}