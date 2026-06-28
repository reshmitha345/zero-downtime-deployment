# 🚀 Zero-Downtime Deployment Pipeline with Canary Releases

A production-style deployment pipeline that updates applications 
without any downtime using Kubernetes Rolling Updates.

## 📌 About the Project

This project demonstrates how to deploy and update applications 
on Kubernetes with zero downtime. When updating from v1 to v2, 
the app stays live throughout the entire update process.

## ✨ Features

- Zero downtime during application updates
- Rolling update strategy with Kubernetes
- Health checks to ensure pods are ready before switching
- Dockerized Flask application
- Multi-replica deployment for high availability

## 🛠️ Tech Stack

- **Python & Flask** — web application
- **Docker** — containerization
- **Kubernetes (Minikube)** — container orchestration
- **kubectl** — Kubernetes command line tool

## 🚀 How to Run

1. Clone the repository
   git clone https://github.com/reshmitha345/zero-downtime-deployment.git

2. Start Minikube
   minikube start --driver=docker

3. Build Docker image
   cd app
   docker build -t reshmitha345/myapp:v1 .

4. Load image into Minikube
   minikube image load reshmitha345/myapp:v1

5. Deploy to Kubernetes
   cd k8s
   kubectl apply -f deployment.yaml
   kubectl apply -f service.yaml

6. Access the app
   minikube service myapp-service --url

## 🔄 How Zero Downtime Works

1. App is running with 3 pods on v1
2. New image v2 is built and loaded
3. Kubernetes updates pods one by one
4. At no point are all pods down
5. App stays live throughout update

## 📸 Rolling Update Command

kubectl set image deployment/myapp myapp=reshmitha345/myapp:v2
kubectl rollout status deployment/myapp
