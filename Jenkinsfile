pipeline {
    agent any

    stages {
        stage('SCM Checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/abhinavthula/gettingstarted.git']])
            }
        }
        stage('Build Docker Image') {
            steps{
                sh 'docker build -t getting-started .'
            }
        }
        stage('Deploy Container') {
            steps{
                sh 'docker rm -f gettingstartedcont'
                sh 'docker run --name gettingstartedcont -dp 3000:3000 getting-started'
            }
        }
    }
}
