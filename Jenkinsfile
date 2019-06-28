pipeline {
    agent { docker { image 'nginx:alpine' } }
    stages {
        stage('build') {
            steps {
                sh 'cp -r ./ /usr/share/nginx/html'
            }
        }
    }
}