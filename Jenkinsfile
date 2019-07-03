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
                    // docker.build  imageName + ":" + imageTag
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


        stage ('Deploy') {
            steps {
                sh 'ssh -i ~/.ssh/scaleway.pem root@51.15.233.87'
                sh 'docker run melioratech/static-web'

                sh 'exit'
            }
        }
    }
}