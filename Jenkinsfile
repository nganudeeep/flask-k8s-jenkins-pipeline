pipeline {
    agent any
    environment {
        IMAGE_NAME = "flask-k8s"
        IMAGE_TAG = "v1"
    }

    stages {
        stage('Build & Load Docker Image inside Minikube') {
            steps {
                sh '''
                    export PATH=$PATH:/usr/local/bin
                    echo "Setting up Minikube Docker environment..."
                    eval $(minikube docker-env)

                    echo "Building Docker image inside Minikube..."
                    docker build -t ${IMAGE_NAME}:${IMAGE_TAG} .
                '''
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh '/usr/local/bin/kubectl apply -f deployment.yaml'
            }
        }

        stage('Verify Deployment') {
            steps {
                sh '/usr/local/bin/kubectl get pods'
                sh '/usr/local/bin/kubectl get svc'
            }
        }
    }
}
