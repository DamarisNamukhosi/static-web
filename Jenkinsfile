pipeline {
    agent { docker { image 'nginx:alpine' } }
    stages {
        stage('build') {
            steps {
                sh 'COPY . /usr/share/nginx/html'
            }
        }
    }
}