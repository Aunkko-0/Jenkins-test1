pipeline {
    agent any

    stages {
        stage('checkout code') {
            steps {
                git branch: 'main',
                    credentialsId: '3ae59fa7-48c2-402d-85e3-f5cb5de0efc3'
                    url: 'https://github.com/Aunkko-0/Jenkins-test1.git'
            }       
        }
        stage('Create file') {
            steps {
                sh 'echo "Automation Pipeline-Github"> touch test1.txt'
            }
        }

        stage('List Files') {
            steps {
                sh 'ls'       
            }
        }
    }
}