# hello-cicd

This project demonstrates a complete CI/CD pipeline from GitHub to Kubernetes using Jenkins, Docker, Helm, and Trivy.  
The goal is to automatically build, scan, push, and deploy a simple Flask application into a K3s cluster using Helm.

---

## 🔧 Tech Stack

- [**GitHub**](https://github.com/) – Source code management
- [**Jenkins**](https://www.jenkins.io/) – CI/CD pipeline
- [**Docker**](https://www.docker.com/) – Containerization
- [**Trivy**](https://aquasecurity.github.io/trivy/) – Security scanning
- [**Docker Hub**](https://hub.docker.com/) – Image registry
- [**Kubernetes (K3s)**](https://k3s.io/) – Lightweight K8s distribution
- [**Helm**](https://helm.sh/) – Kubernetes deployment packaging

---

## 📁 Project Structure

```text
hello-cicd/
├── app.py                         # Flask application
├── Dockerfile                     # Container build file
├── Jenkinsfile                    # Jenkins pipeline definition
├── requirements.txt               # Python dependencies
├── hello-cicd-chart/              # Helm chart for deployment
├── jenkins-pipeline-log.txt       # Jenkins pipeline execution log
├── jenkins-pipeline-readme.txt    # Jenkins explanation
```

---

## 🔄 Pipeline Flow

1. Code is pushed to GitHub.
2. Jenkins pulls the latest code and runs the pipeline:
   - Builds a Docker image of the Flask app.
   - Scans the image using Trivy for critical vulnerabilities.
   - Pushes the image to Docker Hub.
3. Kubernetes pulls the image and deploys it via Helm.
4. The app is exposed using a ClusterIP service.

---

## 📦 Docker Image

- [DockerHub – oren1984/hello-cicd](https://hub.docker.com/r/oren1984/hello-cicd)

---

## 📁 Helm Chart

Helm chart is located at:  
`hello-cicd-chart/`

---

## 🔍 How to Access the App

```bash
kubectl port-forward svc/hello-cicd-release-hello-cicd-chart 5000:5000
```

Then open your browser at:  
👉 [http://localhost:5000](http://localhost:5000)

---

## 👨‍💻 Author

Oren Salami – 2025  
Project submitted as part of Final Project CI/CD track (August)


