# End-to-End CI/CD Pipeline with Jenkins, Docker & Kubernetes

![DevOps](https://img.shields.io/badge/DevOps-CI%2FCD-blue)
![AWS](https://img.shields.io/badge/AWS-EKS%20%7C%20ECR-orange)
![Jenkins](https://img.shields.io/badge/Jenkins-2.479-red)
![Docker](https://img.shields.io/badge/Docker-27.x-blue)
![Kubernetes](https://img.shields.io/badge/Kubernetes-1.31-blue)

## 📌 Project Overview
This project implements a complete end-to-end DevOps CI/CD pipeline that automates 
application build, test, containerization, and deployment to AWS EKS (Elastic 
Kubernetes Service). The pipeline ensures reliable, scalable, and automated 
application delivery with zero manual intervention.

## 🏗️ Architecture
Developer → GitHub → Jenkins → Maven Build → SonarQube → Nexus → Docker → ECR → Kubernetes (EKS)
## 🛠️ Tools & Technologies
| Category | Tools |
|---|---|
| CI/CD | Jenkins |
| Build Tool | Maven |
| Code Quality | SonarQube |
| Artifact Storage | Nexus Repository |
| Containerization | Docker |
| Container Registry | AWS ECR |
| Orchestration | Kubernetes (AWS EKS) |
| Cloud | AWS (EC2, EKS, ECR, IAM, CloudWatch) |
| Version Control | Git, GitHub |

## 📂 Project Structure
├── Jenkinsfile
├── Dockerfile
├── k8s/
   ├── deployment.yaml
   └── service.yaml
└── README.md

## 🔄 Pipeline Stages
1. **Git Checkout** - Pull latest code from GitHub
2. **Maven Build** - Compile and package the application
3. **SonarQube Analysis** - Static code quality analysis
4. **Upload to Nexus** - Store build artifacts
5. **Docker Build** - Create Docker image
6. **Push to ECR** - Push image to AWS Elastic Container Registry
7. **Deploy to EKS** - Deploy to Kubernetes cluster

## ⚙️ Prerequisites
- Jenkins with plugins: Git, Maven, Docker, Kubernetes, SonarQube
- AWS account with EKS cluster configured
- Docker installed on Jenkins agent
- SonarQube server running
- Nexus Repository server running

## 🚀 How to Run
1. Clone this repository
```bash
https://github.com/sanjayt-1503/cicd-jenkins-docker-kubernetes.git
```
2. Configure Jenkins credentials for AWS and Docker
3. Create a Jenkins pipeline job and point to this repo
4. Trigger the pipeline — it will run all stages automatically

## 📊 Monitoring
- AWS CloudWatch Alarms configured for EKS cluster health
- Jenkins build notifications enabled for success/failure alerts

## 👨‍💻 Author
**Sanjay T**
- LinkedIn: https://www.linkedin.com/in/sanjay-t-38a5b4331/
- Email: sanjayt06.off@gmail.com
