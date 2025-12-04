pipeline {
    agent any

    tools {
        dockerTools 'docker-1'
    }

    environment {
        REPO_URL = "https://github.com/Aunkko-0/Jenkins-test1.git"
        REGISTRY_URL = "docker.io"
        IMAGE_NAME   = "jenkins/jenkins"
        GITHUB_USERNAME = "Aunko-0"
        dockerImage  = "${REGISTRY_URL}/${IMAGE_NAME}:latest"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git credentialsId: '3ae59fa7-48c2-402d-85e3-f5cb5de0efc3', url: "${REPO_URL}", branch: 'main'
            }
        }

        stage('Docker Build Release') {
            steps {
               sh """
               docker build \
                -t ${dockerImage} \
                -f services/nest-service/Dockerfile \
                .
                """
            }
        }

        stage('Docker Push') {
            steps {
                echo '------------------------------------------------------------------------------------------------------------'
                withCredentials([string(credentialsId: '3ae59fa7-48c2-402d-85e3-f5cb5de0efc3', variable: 'GITHUB_TOKEN')]) {
                    sh """
                    echo "\$GITHUB_TOKEN" | docker login ${REGISTRY_URL} -u ${GITHUB_USERNAME} --password-stdin
                    docker push ${dockerImage}
                    """
                }
            }
        }
    }
}
