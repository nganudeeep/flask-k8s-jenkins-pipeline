# 🚀 Flask CI/CD Pipeline with Jenkins & Kubernetes

This project automates the deployment of a Flask microservice using Jenkins, Docker, and Kubernetes (via Minikube).  
On every GitHub push, Jenkins builds the Docker image, loads it into Minikube, and applies the Kubernetes deployment.  
The service is exposed via NodePort and accessible in the browser.

🔧 Tech Stack: Flask · Jenkins · Docker · Minikube · Kubernetes · GitHub  
📦 Components: `Dockerfile` · `Jenkinsfile` · `deployment.yaml` · Flask app  
🌐 Access: `minikube service flask-service` opens the app on `localhost`  
✅ Highlights: ImagePull fix, Minikube Docker integration, `CrashLoopBackOff` resolution  
👨‍💻 Author: [nganudeeep](https://github.com/nganudeeep) | [LinkedIn](https://www.linkedin.com/in/n-g-anudeep-2023a2203/)
