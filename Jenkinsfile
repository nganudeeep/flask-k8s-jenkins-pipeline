pipeline {
    agent any
    environment {
        IMAGE_NAME = "flask-k8s"
        IMAGE_TAG = "v1" 
    }

    stages {
        stage('Build Docker Image') {
            steps {
                sh '/usr/local/bin/docker build -t $IMAGE_NAME:$IMAGE_TAG .'
            }
        }

        stage('Load Image into Minikube') {
            steps {
                sh '/usr/local/bin/minikube image load $IMAGE_NAME:$IMAGE_TAG'
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
