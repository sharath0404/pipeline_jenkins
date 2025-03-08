pipeline {
     agent any

    environment {
        KUBECONFIG = credentials('kubeconfig-credentials-id')  // K8s kubeconfig stored as a secret
        DOCKER_CREDENTIALS = credentials('dockerhub-credentials')  // DockerHub credentials stored securely
    }

    stages {
        stage('Checkout Code') { 
            steps {
                git 'https://github.com/sharath0404/k8s.git'
            }
        }

        stage('Build and Push Docker Image') {
            steps {
                script {
                    def imageName = "sharath441993/test:${env.BUILD_NUMBER}"
                    sh "docker build -t ${imageName} ."
                    
                    // Use stored credentials for login
                    sh "echo ${DOCKER_CREDENTIALS_PSW} | docker login -u ${DOCKER_CREDENTIALS_USR} --password-stdin"
                    
                    sh "docker push ${imageName}"
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                script {
                    sh "kubectl apply -f k8s/deployment.yaml"
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                sh "kubectl get pods"
            }
        }
    }
}
