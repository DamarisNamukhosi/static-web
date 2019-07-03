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
                    docker.withRegistry('', 'docker-hub') {
                        dockerImage.push()
                    }
                }                            
            }
        }
    }
}