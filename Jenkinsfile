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
                    // dockerImage = docker.build  imageName + ":" + imageTag
                    dockerImage = sh 'docker build -t melioratech/static-web:latest .'
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
                
                sh 'docker pull melioratech/static-web'
                sh 'docker stop static-web || true && docker rm static-web || true'
                sh 'docker run --name=static-web --restart=always -p 9090:80 -d melioratech/static-web'

                sh 'exit'
            }
        }
    }
}