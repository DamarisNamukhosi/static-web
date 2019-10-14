pipeline {
    environment {
        registryUrl = 'https://registry.hub.docker.com'
        dockerImage = ''
        imageName = 'melioratech/static-web'
        imageTag = 'latest'
    }
    agent any

    stages {

        stage('Build Image - Latest') {
            when {
                expression {
                    return env.GIT_BRANCH != "origin/master"
                }
            }
            
            steps {
                script {
                    dockerImage = docker.build  imageName + ":latest"
                }
            }
        }

        stage('Build Image - Stable') {
            when {
                expression {
                    return env.GIT_BRANCH == "origin/master"
                }
            }

            steps {
                script {
                    dockerImage = docker.build  imageName + ":stable"
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