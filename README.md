# devops-aws-app
📌 Project Overview
CI/CD Flow:
GitHub → Jenkins → Docker → AWS ECR → EC2 → Browser
Whenever code is pushed to GitHub:

Jenkins automatically triggers the pipeline

Docker image is built

Image is pushed to AWS ECR

Container is deployed on an EC2 instance

Application becomes live via public IP
------------------------------------------------------------------------------------------------------------------------------------
🛠️ Tech Stack Used
Version Control: GitHub

CI/CD Tool: Jenkins

Containerization: Docker

Cloud Provider: AWS

Container Registry: Amazon ECR

Compute: Amazon EC2

Authentication: IAM Role (No access keys used)
---------------------------------------------------------------------------------------------------------------------------------------
📂 Project Structure
devops-aws-app/
│
├── index.html        # Web application
├── style.css         # Styling
├── Dockerfile        # Docker image definition
└── Jenkinsfile       # Jenkins CI/CD pipeline
-----------------------------------------------------------------------------------------------------------------------------------------
⚙️ Jenkins Pipeline Stages
1. Source Code Checkout – Pulls code from GitHub
2. Build Docker Image – Creates Docker image from Dockerfile
3. Authenticate with ECR - Uses IAM Role for secure access
4. Push Image to ECR – Uploads image to AWS ECR
5. Deploy on EC2 – Runs container and exposes application
---------------------------------------------------------------------------------------------------------------------------------------------
🔐 Security Best Practices
Used IAM Role attached to EC2 instead of hardcoding AWS credentials

No AWS access key or secret key stored in Jenkins

Followed least-privilege access principle
-------------------------------------------------------------------------------------------------------------------------------------
