pipeline {
    agent any

    stages {
        stage('Build docker image') {
            steps {
                script {
                    sh 'docker build -t amr/docker-react -f Dockerfile.dev .'
                }
            }
        }

        stage('Run tests') {
            steps {
                script {
                    sh 'DOCKER_BUILDKIT=1 docker run --rm -e CI=true amr/docker-react npm run test'
                }
            }
        }
    }
}