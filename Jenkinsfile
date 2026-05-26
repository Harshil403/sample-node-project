pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git branch: 'dev',
                url: 'https://github.com/Harshil403/sample-node-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t sample-node-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                docker stop sample-node-container || true
                docker rm sample-node-container || true
                docker run -d -p 3000:3000 --name sample-node-container sample-node-app
                '''
            }
        }
    }
}
