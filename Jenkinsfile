pipeline {
    agent { docker { image 'nginx:alpine' } }
    stages {
        stage('build') {
            steps {
                sh 'cp . /usr/share/nginx/html'
            }
        }
    }
}