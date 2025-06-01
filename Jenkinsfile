pipeline {
    agent any
    environment {
        IMAGE_NAME = "flask-k8s"
        IMAGE_TAG = "v1"
    }

    stages {
        stage('Use Minikube Docker') {
            steps {
                // Point Jenkins to Minikube's Docker
                sh 'eval $(/usr/local/bin/minikube docker-env)'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME:$IMAGE_TAG .'
            }
        }

        stage('Load Image into Minikube') {
            steps {
                // Optional if image was built inside Minikube
                sh 'minikube image load $IMAGE_NAME:$IMAGE_TAG'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
            }
        }

        stage('Verify Deployment') {
            steps {
                sh 'kubectl get pods'
                sh 'kubectl get svc'
            }
        }
    }
}
