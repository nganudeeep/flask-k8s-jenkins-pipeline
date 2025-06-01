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
                    echo "Setting up Minikube Docker environment..."
                    eval $(/usr/local/bin/minikube docker-env)

                    echo "Building Docker image inside Minikube..."
                    docker build -t ${IMAGE_NAME}:${IMAGE_TAG} .

                    echo "Docker image built: ${IMAGE_NAME}:${IMAGE_TAG}"
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
