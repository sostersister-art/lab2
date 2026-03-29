pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/sostersister-art/lab2.git'
            }
        }

        stage('SonarQube analysis') {
            steps {
                script {
                    def scannerHome = tool 'SonarQube Scanner'
                    withSonarQubeEnv('SonarQube') {
                        sh "${scannerHome}/bin/sonar-scanner"
                    }
                }
            }
        }

        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build || true'
            }
        }
    }
}
