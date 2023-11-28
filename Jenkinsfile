pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/m0719/jenkinswork.git'
            }
        }
        
        stage('Build and Test') {
            steps {
                script {
                    // Assuming docker-compose.yml is in the root directory of the repository
                    bat 'docker-compose up -d'  // Use -d for detached mode, if needed
                }
            }
        }

        stage('SonarQube Scan') {
            steps {
                withSonarQubeEnv('sonarqube-server') {
                    script {
                        bat 'sonar-scanner' // Or use 'sh' for Linux-based systems
                    }
                }
            }
        }
    }
}
