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

        stage('Git Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: '3ae59fa7-48c2-402d-85e3-f5cb5de0efc3', passwordVariable: 'MY_PASS', usernameVariable: 'MY_USER')])
                    sh """
                        git config user.email "tanapol1108@gmail.com"
                        git config user.name "Aunkko-0"

                        git add test1.txt
                       git commit -m "Add test1.txt from Jenkins Pipeline"

                        git push https://${MY_USER}:${MY_PASS}@github.com/Aunkko-0/Jenkins-test1.git HEAD:main
                    """
                }
            }
        }    
        
        stage('List Files') {
            steps {
                sh 'ls -la'       
            }
        }
    }
}
