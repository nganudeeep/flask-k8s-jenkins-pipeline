pipeline {
    agent any
    environment {
        IMAGE_NAME = "flask-k8s"
    }

    stages {
        stage('Build Docker Image') {
            steps {
                echo "🔨 Building Docker image..."
                sh '/usr/local/bin/docker build -t $IMAGE_NAME .'
            }
        }

        stage('Load Image into Minikube') {
            steps {
                echo "📦 Loading image into Minikube..."
                sh '/usr/local/bin/minikube image load $IMAGE_NAME'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                echo "🚀 Deploying to Kubernetes..."
                sh '/usr/local/bin/kubectl apply -f deployment.yaml'
            }
        }

        stage('Verify Deployment') {
            steps {
                echo "🔍 Checking Kubernetes resources..."
                sh '/usr/local/bin/kubectl get pods'
                sh '/usr/local/bin/kubectl get svc'
            }
        }
    }
}
