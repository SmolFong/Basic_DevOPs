pipeline {
    agent any
    environment {
        DOCKER_HUB_USER = "thanhphong2612" 
        IMAGE_NAME = "DevOps"
        DOCKER_HUB_CREDS = 'docker-hub-credentials'
    }
    stages {
        stage('1. Sync Source') {
            steps {
                checkout scm
            }
        }
        stage('2. Build & Push Image') {
            steps {
                script {
                    def appImage = docker.build("${DOCKER_HUB_USER}/${IMAGE_NAME}")
                    docker.withRegistry('', DOCKER_HUB_CREDS) {
                        appImage.push("latest")
                    }
                }
            }
        }
        stage('3. Run Application') {
            steps {
                sh "docker rm -f ${IMAGE_NAME} || true"
                sh "docker run -d --name ${IMAGE_NAME} -p 8081:80 ${DOCKER_HUB_USER}/${IMAGE_NAME}:latest"
            }
        }
    }
}
