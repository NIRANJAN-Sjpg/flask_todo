pipeline {
    agent any
    evironment{
        IMAGE_NAME ='ninja1234567/flask_todo'
    }
    stages {
        stage('checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/NIRANJAN-Sjpg/flask_todo'
            }
        }

        stage('build docker image') {
            steps {
                bat "docker build -t %IMAGE_NAME%:LATEST ."
                
            }
        }

        stage('PUSH') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker',usernameVariable: 'DOCKER_USER',passwordVariable: 'DOCKER_PASS)]){
                                                  bat """
                                                 echo %DOCKER_PASS% |
                                                 docker login -u %DOCKER_USER% --password-stdin
                                                 docker push %IMAGE_NAME%:latest
                                                 docker logout
                                                 ___
            }
        }
    }
}
}
