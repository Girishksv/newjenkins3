pipeline {
    agent any

    environment {
        DOCKER_CREDENTIALS_ID = 'creddocker'
        DOCKER_IMAGE = 'proj3'
        
    }

    stages {
        stage('git') {
            steps {
                git branch: 'master',url: 'https://github.com/Girishksv/newjenkins3.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'creddocker', usernameVariable: 'girish789', passwordVariable: 'Girish@789')]) {
                    script {
                        bat 'docker stop cont3'
                        bat 'docker rm cont3'
                        bat 'docker rmi proj3'
                        bat 'docker build -t proj3 .'
                        bat 'docker run -d --name cont3 -p 8050:80 proj3'
                    }
                }
            }
        }
    }
}
