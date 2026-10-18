pipeline {
    agent {
        label 'docker'
    }

    stages {
        stage('Build Docker image') {
            steps {
                script {
                    sh 'docker build -t amrnagy74/docker-react -f Dockerfile.dev .'
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    env.DOCKER_BUILDKIT = 1
                    sh 'docker run -e CI=true amrnagy74/docker-react npm run test'
                }
            }
        }
    }
}