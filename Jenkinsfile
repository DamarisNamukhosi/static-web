pipeline {
    agent any
    stages {
        stage('Build Image') {
            steps {
                // input message: 'Finished using the web site? (Click "Proceed" to continue)'
                // sh 'cp -r ./ /usr/share/nginx/html'
                sh "docker build -t melioratech/static-web ."
            }
        }

        stage('Push image') {
            steps {
                withDockerRegistry([credentialsId: 'docker-hub', url: 'https://registry.hub.docker.com']) {
                    sh "docker push melioratech/static-web:latest"
                }                              
            }
        }
    }
}