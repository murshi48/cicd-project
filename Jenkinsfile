pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                git 'https://github.com/murshi48/cicd-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myapp .'
            }
        }

        stage('Stop & Remove Old Container') {
            steps {
                sh 'docker stop myapp || true'
                sh 'docker rm myapp || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d -p 80:5000 --name myapp myapp'
            }
        }
    }
}
