pipeline {
    agent {
        label 'ubuntuwrk'
    }
    stages {
        stage('verify installation') {
            steps {
                sh '''
                    docker version
                    docker info
                    docker-compose version
                    curl --version
                    jq --version
                '''
            }
        }
        stage('prune docker data') {
            steps {
                sh 'docker volume prune -f'
            }
        }
        stage('starting container') {
            steps {
                sh 'docker-compose up'
                sh 'docker-compose ps'
            }
        }
    }
}
