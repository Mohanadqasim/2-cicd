# 2-cicd - CI/CD pipeline using Flask, Docker, ECR and EC2
CI/CD Pipeline using Flask, Docker, Amazon ECR, EC2 and GitHub Actions

---

## 📌 Project Overview

This project demonstrates a complete CI/CD pipeline for a containerized Flask application deployed on AWS.

Whenever code is pushed to the `main` branch:

1. GitHub Actions builds a Docker image
2. The image is pushed to Amazon ECR
3. GitHub connects to EC2 via SSH
4. The running container is stopped
5. The latest image is pulled from ECR
6. The application is redeployed automatically

Deployment happens without manual intervention.

---

## 🏗 Architecture

Developer → GitHub → GitHub Actions → Amazon ECR → EC2 → Docker Container

---

## 🧰 Technologies Used

- Python (Flask)
- Docker
- Amazon EC2
- Amazon ECR
- GitHub Actions
- SSH-based deployment

---
## 📂 Project Structure
2-cicd/

├── .github/workflows/

│ └── deploy.yml
│

├── app/
│ ├── app.py

│ └── requirements.txt
│

├── Dockerfile

├── .gitignore

└── README.md

---

## 🚀 How Deployment Works

### 1️⃣ Code Push
Changes are pushed to the `main` branch.

### 2️⃣ GitHub Actions Pipeline
The workflow:
- Logs into AWS
- Builds Docker image
- Tags image as `latest`
- Pushes image to ECR

### 3️⃣ SSH Deployment
GitHub:
- Connects to EC2 using a stored private SSH key
- Pulls the latest image from ECR
- Stops and removes the running container
- Starts a new container

---

## 🔐 Security Practices

- SSH private key stored in GitHub Secrets
- EC2 IAM role used for ECR access
- Sensitive files excluded using `.gitignore`
- No secrets stored in the repository

---

## 🧠 Final Note

Automation is not about speed.  
It is about reliability, repeatability, and removing human error from deployment.

If it requires manual SSH to deploy, it is not CI/CD.