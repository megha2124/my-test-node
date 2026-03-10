pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/megha2124/my-test-node.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-node:${BUILD_NUMBER} .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop my-app || true'
                sh 'docker rm my-app || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d -p 3000:3000 --name my-app my-node:${BUILD_NUMBER}'
            }
        }
    }
}