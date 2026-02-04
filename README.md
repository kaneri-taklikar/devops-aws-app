a# devops-aws-app
# 🚀 DevOps CI/CD Pipeline using Jenkins, Docker & AWS ECR

## 📌 Project Overview

This project demonstrates a **complete CI/CD pipeline** using **Jenkins, Docker, and AWS services**. The application code is stored on GitHub, automatically built and containerized by Jenkins, pushed to AWS Elastic Container Registry (ECR), and deployed on an EC2 instance.

This project follows **real industry DevOps practices**, including secure authentication using **IAM Roles** instead of hardcoded credentials.

---

## 🛠️ Tools & Technologies Used

* **GitHub** – Source code management
* **Jenkins** – CI/CD automation
* **Docker** – Containerization
* **AWS EC2** – Jenkins & application hosting
* **AWS ECR** – Docker image registry
* **IAM Role** – Secure AWS authentication

---

## 🧱 Architecture Flow

```
GitHub → Jenkins → Docker Image → AWS ECR → EC2 (Live Application)
```

---

## ⚙️ Project Setup & Commands Used

### 1️⃣ Clone the GitHub Repository

```bash
git clone https://github.com/kaneri-taklikar/devops-aws-app.git
cd devops-aws-app
```

---

### 2️⃣ Install Docker

```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
```

---

### 3️⃣ Build Docker Image

```bash
docker build -t devops-app .
```

✔️ This command creates a Docker image named `devops-app` using the Dockerfile present in the project directory.

---

### 4️⃣ Create AWS ECR Repository

```bash
aws ecr create-repository \
--repository-name devops-app \
--region ap-south-1
```

✔️ This creates a private Docker repository in AWS ECR (Mumbai region).

---

### 5️⃣ Login to AWS ECR (Using IAM Role)

```bash
aws ecr get-login-password --region ap-south-1 \
| docker login --username AWS --password-stdin 530946467712.dkr.ecr.ap-south-1.amazonaws.com
```

✔️ Jenkins/EC2 authenticates securely using an **IAM Role** (no AWS keys used).

---

### 6️⃣ Tag Docker Image for ECR

```bash
docker tag devops-app:latest \
530946467712.dkr.ecr.ap-south-1.amazonaws.com/devops-app:latest
```

✔️ Tags the local image with the AWS ECR repository URI.

---

### 7️⃣ Push Docker Image to AWS ECR

```bash
docker push 530946467712.dkr.ecr.ap-south-1.amazonaws.com/devops-app:latest
```

✔️ Uploads the Docker image to AWS ECR.

---

## 🔁 Jenkins CI/CD Pipeline

* Jenkins is installed on an EC2 instance
* GitHub webhook triggers the pipeline
* Jenkinsfile defines stages:

  * Code checkout
  * Docker image build
  * ECR login
  * Image tag & push

✔️ Entire process is automated.

---

## 🔐 Security Best Practices Followed

* No AWS Access Keys or Secrets hardcoded
* IAM Role attached to Jenkins EC2 instance
* Secure authentication with AWS services

---

## 🌐 Final Output

* Docker image successfully pushed to AWS ECR
* Application running live on EC2
* CI/CD pipeline completed successfully

---

## 🧑‍💻 Author

**Kaneri Taklikar**
DevOps Enthusiast | AWS | Docker | Jenkins

---

## 📎 Screenshots

* Jenkins Pipeline Success
* AWS ECR Repository
* Live Application Output

(Attached in LinkedIn post)

---

✨ *This project reflects hands-on DevOps experience with real-world tools and workflows.*
