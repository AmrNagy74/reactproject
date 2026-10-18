pipeline {
    agent{
        label 'docker'
    }
}

stages {
    stage('Build docker image') {
        steps {
            script {
               sh 'docker.build -t amr/docker-react -f Dockerfile.dev . '
            }
        }
    }
}

stage('Run tests') {
    steps {
        script {
            env.Docker_BUILDKIT=1
            sh 'docker run --rm -e CI=true amr/docker-react npm test'
        }
    }
}

