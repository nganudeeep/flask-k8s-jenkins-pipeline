pipeline {
    agent any
    environment {
        IMAGE_NAME = "flask-k8s"
    }

    stages {
        stage('Build Docker Image') {
            steps {
                echo "Building Docker image..."
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Load Image into Minikube') {
            steps {
                echo "Loading image into Minikube..."
                sh 'minikube image load $IMAGE_NAME'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                echo "Applying Kubernetes manifests..."
                sh 'kubectl apply -f deployment.yaml'
            }
        }

        stage('Verify Deployment') {
            steps {
                echo "Deployment details:"
                sh 'kubectl get pods'
                sh 'kubectl get svc'
            }
        }
    }
}
