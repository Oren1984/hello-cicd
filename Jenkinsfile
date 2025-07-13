pipeline {
    agent any 

    environment {
        IMAGE_NAME = 'hello-cicd'
        IMAGE_TAG = 'latest'
        DOCKER_USER = 'oren692'  
        GIT_REPO_URL = 'https://github.com/Oren1984/hello-cicd.git'
    }

    stages {
        stage('Checkout SCM') {
            steps {
                echo "Cloning from repository: ${GIT_REPO_URL}"
                echo "Project: ${IMAGE_NAME}"
                // Checkout the 'main' branch explicitly
                checkout([$class: 'GitSCM', branches: [[name: 'refs/heads/main']], extensions: [], userRemoteConfigs: [[url: GIT_REPO_URL]]])
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t ${IMAGE_NAME}:${IMAGE_TAG} ."
            }
        }

        stage('Scan with Trivy') {
            steps {
                echo 'Scanning Docker image for vulnerabilities (critical/high)...'
                sh "trivy image --scanners vuln --severity CRITICAL,HIGH --no-progress ${IMAGE_NAME}:${IMAGE_TAG}"
            }
        }

        stage('Push to Docker Hub') {
            steps {
                echo 'Pushing image to Docker Hub...'
                withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'DOCKER_USER_VAR', passwordVariable: 'DOCKER_PASS')]) {
                    sh '''
                        echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER_VAR" --password-stdin
                        docker tag ${IMAGE_NAME}:${IMAGE_TAG} docker.io/$DOCKER_USER/${IMAGE_NAME}:${IMAGE_TAG}
                        docker push docker.io/$DOCKER_USER/${IMAGE_NAME}:${IMAGE_TAG}
                        docker logout
                    '''
                }
            }
        }

        stage('Run Container') {
            steps {
                echo 'Removing existing container (if any)...'
                sh "docker rm -f ${IMAGE_NAME}-container || true"
                echo 'Running new container...'
                sh "docker run -d --name ${IMAGE_NAME}-container -p 5000:5000 ${IMAGE_NAME}:${IMAGE_TAG}"
            }
        }
    }

    post {
        always {
            echo "Cleaning up after build..."
            sh "docker stop ${IMAGE_NAME}-container || true"
            sh "docker rm ${IMAGE_NAME}-container || true"
        }
    }
}
