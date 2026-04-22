pipeline {
    agent any
    triggers {
        pollSCM('* * * * *') 
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/anujsharma6y-ctrl/Jenkins-test.git'
            }
        }
        stage('Build & Deploy') {
            steps {
                sh 'docker build -t my-app:latest .'
                sh 'docker rm -f my-running-app || true'
                sh 'docker run -d -p 5000:5000 --name my-running-app my-app:latest'
            }
        }
    }
}
