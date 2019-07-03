pipeline {
    def dockerImage
    agent { docker { image 'nginx:alpine' } }
    stages {
        stage('Build Image') {
            steps {
                // input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh 'cp -r ./ /usr/share/nginx/html'
                dockerImage = docker.build("melioratech/static-web")
            }
        }

        stage('Push image') {
            docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
            dockerImage.push()
        }
  }
    }
}