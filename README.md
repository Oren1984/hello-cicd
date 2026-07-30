# Hello CI/CD

End-to-end CI/CD pipeline from GitHub to Kubernetes using Jenkins, Docker, Helm, and Trivy.

---

## Overview

A complete DevOps pipeline that builds, scans, pushes, and deploys a Flask application to a Kubernetes (K3s) cluster.

---

## Tech Stack

- GitHub
- Jenkins
- Docker
- Trivy
- Docker Hub
- Kubernetes (K3s)
- Helm

---

## Quick Start

Build and run locally (optional):

```bash
docker build -t hello-cicd .
docker run -p 5000:5000 hello-cicd
```

Deploy to Kubernetes:

```bash
helm install hello-cicd-release ./hello-cicd-chart
```

Access the app:

```bash
kubectl port-forward svc/hello-cicd-release-hello-cicd-chart 5000:5000
```

Open: http://localhost:5000

---

## Usage

Pipeline flow:

- Code pushed to GitHub

- Jenkins pipeline runs automatically

- Docker image is built

- Trivy scans for vulnerabilities

- Image is pushed to Docker Hub

- App is deployed to Kubernetes via Helm

---

## Cleanup

```bash
helm uninstall hello-cicd-release
```

---

## Notes

- Built as a practical CI/CD and Kubernetes demonstration
- Includes automated container vulnerability scanning with Trivy
- Uses Helm for repeatable Kubernetes deployment

---
