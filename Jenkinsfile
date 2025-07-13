pipeline {
    agent any

    environment {
        IMAGE_NAME = 'hello-cicd'
        IMAGE_TAG = 'latest'
        GIT_REPO_URL = 'https://github.com/Oren1984/hello-cicd.git'
    }

    stages {
        stage('Print Git Repo URL') {
            steps {
                echo "Cloning from repository: ${GIT_REPO_URL}"
                echo "Project: $IMAGE_NAME"
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t $IMAGE_NAME:$IMAGE_TAG ."
            }
        }

        stage('Scan with Trivy') {
            steps {
                sh "trivy image --severity CRITICAL,HIGH --no-progress $IMAGE_NAME:$IMAGE_TAG || true"
            }
        }

        stage('Run Container') {
            steps {
                sh "docker run -d --name ${IMAGE_NAME}-container -p 5000:5000 $IMAGE_NAME:$IMAGE_TAG"
            }
        }
    }

    post {
        always {
            echo "Cleaning up container..."
            sh "docker stop ${IMAGE_NAME}-container || true"
            sh "docker rm ${IMAGE_NAME}-container || true"
        }
    }
}
pipeline {
    agent { label 'worker' }

    environment {
        IMAGE_NAME = 'hello-cicd'
        IMAGE_TAG = 'latest'
        GIT_REPO_URL = 'https://github.com/Oren1984/hello-cicd.git'
    }

    stages {
        stage('Print Git Repo URL') {
            steps {
                echo "Cloning from repository: ${GIT_REPO_URL}"
                echo "Project: $IMAGE_NAME"
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t $IMAGE_NAME:$IMAGE_TAG ."
            }
        }

        stage('Scan with Trivy') {
            steps {
                sh "trivy image --severity CRITICAL,HIGH --no-progress $IMAGE_NAME:$IMAGE_TAG || true"
            }
        }

        stage('Run Container') {
            steps {
                sh "docker run -d --name ${IMAGE_NAME}-container -p 5000:5000 $IMAGE_NAME:$IMAGE_TAG"
            }
        }
    }

    post {
        always {
            echo "Cleaning up container..."
            sh "docker stop ${IMAGE_NAME}-container || true"
            sh "docker rm ${IMAGE_NAME}-container || true"
        }
    }
}
