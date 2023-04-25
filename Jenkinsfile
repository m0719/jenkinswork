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
                sh 'docker system prune -f'
            }
        }
        stage('starting container') {
            steps {
                sh 'mkdir /home/ubuntu20/jenkinswork2'
                sh 'cd /home/ubuntu20/jenkinswork2/ '
                sh 'touch /home/ubuntu20/jenkinswork2/testjn.txt'
                sh 'docker-compose -f /home/ubuntu20/jenkinswork/docker-compose.yaml up -d'
                sh 'docker ps -a'
            }
        }
    }
}
