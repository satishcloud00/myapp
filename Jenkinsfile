pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/USERNAME/REPOSITORY.git'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t myapp:v1 .'
            }
        }

        stage('Docker Login') {
            steps {
                sh 'docker login -u YOUR_USERNAME -p YOUR_PASSWORD'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                sh 'docker tag myapp:v1 YOUR_USERNAME/myapp:v1'
                sh 'docker push YOUR_USERNAME/myapp:v1'
            }
        }
    }
}
