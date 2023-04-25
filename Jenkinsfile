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
                sh 'mkdir /home/ubuntu20/jenkinswork'
                sh 'cd /home/ubuntu20/jenkinswork/ '
                sh 'touch /home/ubuntu20/jenkinswork/testjn.txt'
                sh 'cd ~/jenkinswork
                sh 'docker-compose up -d'
                sh 'docker-compose -f ~/jenkinswork/docker-compose.yaml up -d'
                sh 'docker ps -a'
            }
        }
    }
}
