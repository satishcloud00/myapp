
pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/USERNAME/REPOSITORY.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myapp:v1 .'
            }
        }

        stage('Login to Docker Hub') {
            steps {
                sh 'docker login -u YOUR_DOCKER_USERNAME -p YOUR_DOCKER_PASSWORD'
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker tag myapp:v1 YOUR_DOCKER_USERNAME/myapp:v1'
                sh 'docker push YOUR_DOCKER_USERNAME/myapp:v1'
            }
        }
    }
}
