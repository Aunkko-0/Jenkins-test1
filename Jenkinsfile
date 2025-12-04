pipeline {
    agent any

    stages {
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