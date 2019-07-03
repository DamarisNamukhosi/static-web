pipeline {
    agent { docker { image 'nginx:alpine' } }
    stages {
        stage('build') {
            steps {
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh 'cp -r ./ /usr/share/nginx/html'
            }
        }
    }
}