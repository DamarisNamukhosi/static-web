node {
    checkout scm
    def dockerImage

    stage ('Build Image'){
        dockerImage = docker.build("melioratech/static-web", "src/docker/Dockerfile");
    }


    stage ('Push Image') {
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
            input message: 'Are you sure you want to push the image to Registry? (Click "OK" to continue)'
            dockerImage.push()
        }
    }
}