pipeline {
    agent any

    tools {
        maven 'Maven-3.9'
    }

    environment {
        DOCKER_IMAGE = 'your-dockerhub-username/myapp'
        DOCKER_TAG = "${BUILD_NUMBER}"
        ECR_REGISTRY = 'your-aws-account-id.dkr.ecr.ap-south-1.amazonaws.com'
    }

    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/your-username/your-repo.git'
            }
        }

        stage('Maven Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh 'mvn sonar:sonar'
                }
            }
        }

        stage('Upload to Nexus') {
            steps {
                sh 'mvn deploy -DskipTests'
            }
        }

        stage('Docker Build') {
            steps {
                sh "docker build -t ${DOCKER_IMAGE}:${DOCKER_TAG} ."
            }
        }

        stage('Docker Push to ECR') {
            steps {
                sh """
                    aws ecr get-login-password --region ap-south-1 | \
                    docker login --username AWS --password-stdin ${ECR_REGISTRY}
                    docker tag ${DOCKER_IMAGE}:${DOCKER_TAG} ${ECR_REGISTRY}/myapp:${DOCKER_TAG}
                    docker push ${ECR_REGISTRY}/myapp:${DOCKER_TAG}
                """
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh """
                    aws eks update-kubeconfig --region ap-south-1 --name my-eks-cluster
                    kubectl apply -f k8s/deployment.yaml
                    kubectl apply -f k8s/service.yaml
                """
            }
        }
    }

    post {
        success {
            echo 'Deployment Successful!'
        }
        failure {
            echo 'Deployment Failed!'
        }
    }
}
