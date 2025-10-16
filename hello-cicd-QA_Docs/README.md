#  QA Documentation – Hello CI/CD Project

This folder contains all QA documentation and verification results  
based on **Jenkins build logs**, **Docker image analysis**, and **Trivy security scans**.

---

## 📄 Documents Overview

| File | Description |
|------|--------------|
| **01_STP_Test_Plan.xlsx** | Overall test plan for the CI/CD pipeline |
| **02_STD_Test_Cases.xlsx** | Detailed test cases (Build, Push, Scan, Run) |
| **03_STR_Test_Report.xlsx** | Summary of Jenkins & Trivy execution results |
| **04_Bug_Report.xlsx** | Security vulnerabilities identified by Trivy |
| **📁 Jenkins_Logs/** | Raw execution logs from Jenkins pipeline runs |

---

## 🧰 Jenkins Execution Logs

All Jenkins pipeline execution logs are stored under  
`QA_Docs/Jenkins_Logs/` for reference and verification of the following stages:

- Git checkout and build initialization  
- Docker image build and tagging  
- Trivy vulnerability scan  
- Docker Hub push and container deployment  
- Cleanup and pipeline completion

These logs serve as real execution evidence for CI/CD validation.

---

## ✅ Summary

All pipeline stages finished **successfully**,  
with **one critical vulnerability (zlib1g)** detected in the Trivy scan.

The QA documentation reflects a **Quality-Driven DevOps approach**,  
emphasizing traceability, reproducibility, and detailed reporting.
