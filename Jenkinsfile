node {
    checkout scm
    def dockerImage

    stage ('Build Image'){
        dockerImage = docker.build("melioratech/static-web");
    }


    stage ('Push Image') {
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
            dockerImage.push()
        }
    }
}