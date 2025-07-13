# hello-cicd

This project demonstrates a complete CI/CD pipeline from GitHub to Kubernetes using Jenkins, Docker, Helm, and Trivy.


## 🔧 Stack

- GitHub
- Jenkins
- Docker
- Trivy (Security Scan)
- Docker Hub
- Kubernetes (K3s)
- Helm


## 🚀 Pipeline Flow

1. Code is pushed to GitHub
2. Jenkins pulls the latest code and runs the pipeline:
   - Builds Docker image of Flask app
   - Scans image for vulnerabilities using Trivy
   - Pushes the image to Docker Hub
3. Kubernetes cluster pulls the image and deploys it via Helm
4. Application is exposed using a ClusterIP service


## 📦 Docker Image

- [DockerHub – oren1984/hello-cicd](https://hub.docker.com/r/oren1984/hello-cicd)


## 📁 Helm Chart

Helm chart is located in: `hello-cicd-chart/`


## 🔍 How to Access App

```bash
kubectl port-forward svc/hello-cicd-release-hello-cicd-chart 5000:5000



Then open your browser at:
👉 http://localhost:5000


📝 Project Status
✅ Final Project – CI/CD (Basic Part): Completed


