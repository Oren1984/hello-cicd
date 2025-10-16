#  Hello CI/CD – Final Project (August 2025)

This project demonstrates a complete **CI/CD pipeline** from GitHub to Kubernetes (K3s),  
using **Jenkins, Docker, Helm, and Trivy** to automate build, security scan, push, and deployment  
of a simple **Flask web application**.

---

## 🔧 Tech Stack

[**GitHub**](https://github.com) – Source code management  
- [**Jenkins**](https://www.jenkins.io) – CI/CD pipeline automation  
- [**Docker**](https://www.docker.com) – Containerization  
- [**Trivy**](https://aquasecurity.github.io/trivy) – Image security scanning  
- [**Docker Hub**](https://hub.docker.com) – Image registry  
- [**Kubernetes (K3s)**](https://k3s.io) – Lightweight Kubernetes distribution  
- [**Helm**](https://helm.sh) – Deployment packaging and management   

---

## 📁 Project Structure
```plaintext
hello-cicd/
├── app.py # Flask application
├── Dockerfile # Container build file
├── Jenkinsfile # Jenkins pipeline definition
├── requirements.txt # Python dependencies
├── hello-cicd-chart/ # Helm chart for deployment
│ ├── templates/ # Deployment, Service, Ingress, HPA, etc.
│ ├── values.yaml # Helm configuration
│ └── Chart.yaml # Chart metadata
├── QA_Docs/ # QA documentation and Jenkins logs
│ ├── Jenkins_Logs/
│ │ ├── jenkins-pipeline-log.txt
│ │ └── jenkins-pipeline-readme.txt
│ ├── 01_STP_Test_Plan.xlsx
│ ├── 02_STD_Test_Cases.xlsx
│ ├── 03_STR_Test_Report.xlsx
│ ├── 04_Bug_Report.xlsx
│ └── README.md


---

## 🔄 Pipeline Flow

1. **Code Push** → Developer commits changes to GitHub.  
2. **Jenkins CI/CD** pipeline triggers automatically:  
   - 🏗️ Builds a Docker image from `Dockerfile`.  
   - 🔍 Scans the image with **Trivy** for vulnerabilities.  
   - 🚀 Pushes the image to **Docker Hub**.  
   - ☸️ Deploys to **Kubernetes (K3s)** via **Helm**.  
3. **Cluster** exposes the app via a `ClusterIP` service.  

✅ *All stages completed successfully, with one critical vulnerability (zlib1g) detected.*

---

## 🧪 Quality Assurance (QA)

Comprehensive QA documentation is included under `QA_Docs/`  
to ensure traceability, reproducibility, and test validation.

| Document | Description |
|-----------|-------------|
| **01_STP_Test_Plan.xlsx** | Overall CI/CD test plan |
| **02_STD_Test_Cases.xlsx** | Detailed test case documentation (Build, Push, Scan, Run) |
| **03_STR_Test_Report.xlsx** | Results summary from Jenkins & Trivy |
| **04_Bug_Report.xlsx** | Vulnerabilities and remediation status |
| **Jenkins_Logs/** | Raw execution logs for verification |

📘 *All QA documents are based directly on real Jenkins and Trivy output for accuracy.*

---

## 📦 Docker Image

**Docker Hub:** [oren1984/hello-cicd](https://hub.docker.com/r/oren1984/hello-cicd)

---

## 🧭 Deployment (Helm on K3s)

Deploy with:
```bash
helm install hello-cicd-release ./hello-cicd-chart


Access locally:

kubectl port-forward svc/hello-cicd-release-hello-cicd-chart 5000:5000


Then open:
👉 http://localhost:5000

👨‍💻 Author

Oren Salami – 2025
Project submitted as part of Final Project – CI/CD Track (August)

