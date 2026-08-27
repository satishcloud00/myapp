pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/satishcloud00/myapp.git'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t myapp:v1 .'
            }
        }

        stage('Docker Login') {
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: 'dockerhub-creds-new',
                        usernameVariable: 'DOCKER_USER',
                        passwordVariable: 'DOCKER_TOKEN'
                    )
                ]) {
                    sh 'echo "$DOCKER_TOKEN" | docker login -u "$DOCKER_USER" --password-stdin'
                }
            }
        }

        stage('Push Image') {
          steps {
             sh 'docker tag myapp:v1 satishvasre/myapp:v1'
             sh 'docker push satishvasre/myapp:v1'
    }
}
    }
}
