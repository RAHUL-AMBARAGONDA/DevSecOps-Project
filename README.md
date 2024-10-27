#H1 End-to-End DevSecOps Pipeline for Super Mario Game (Largest)

# **Table of Contents**

- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Project Overview](#project-overview)
- [Pipeline Architecture](#pipeline-architecture)
- [Step-by-Step Implementation](#step-by-step-implementation)
  - [1. Clone the Repository](#1-clone-the-repository)
  - [2. Set Up GitHub Actions](#2-set-up-github-actions)
  - [3. Configure SonarQube for SAST](#3-configure-sonarqube-for-sast)
  - [4. Dockerize the Mario Game](#4-dockerize-the-mario-game)
  - [5. Implement Dynamic Tagging](#5-implement-dynamic-tagging)
  - [6. Deploy to AKS with ArgoCD](#6-deploy-to-aks-with-argocd)
  - [7. Validate End-to-End Pipeline Execution](#7-validate-end-to-end-pipeline-execution)
- [Conclusion](#conclusion)
- [License](#license)

**Project Introduction:** Secure DevSecOps Pipeline for Infinite Mario Game
In this project, we establish a secure, automated DevSecOps pipeline to manage the development, security, and deployment lifecycle of the Infinite Mario JavaScript game. This project demonstrates the full DevSecOps workflow, from code quality checks and security scans to seamless container deployment in a Kubernetes environment. By implementing a robust CI/CD process, we enable automated detection of vulnerabilities, streamlined deployments, and secure infrastructure, all in a highly adaptable, cloud-based setup.

**This project aims to deliver:**

Automated Code Quality and Security: Integration with SonarQube for Static Application Security Testing (SAST) to ensure high code quality and detect potential security issues at an early stage.
Container Security: Use of Trivy and other tools to scan for vulnerabilities in container images before deployment.
Infrastructure-as-Code (IaC): Efficient deployment and management of the Infinite Mario game within Azure Kubernetes Service (AKS), allowing rapid scaling and seamless updates.
Continuous Deployment: Leverage GitHub Actions workflows to automate CI/CD processes, ensuring rapid and reliable releases with every code change.

**Project Prerequisites**

**To get started with this project, ensure that the following prerequisites are met:**

**Azure Account:** An active Azure account with a free or paid subscription. Sign up here for a free trial if needed.

**Azure Kubernetes Service (AKS):** Knowledge of creating and managing Kubernetes clusters in Azure.
Docker Hub Account: A Docker Hub account to store and manage container images.

**Docker CLI:** Installed on your local machine to build and push images. Get Docker CLI here.
GitHub Account: GitHub repository with Actions enabled for automating CI/CD workflows.

**SonarQube:** An active SonarQube instance or account for running SAST scans.

**SonarQube Tokens:** For authentication and integration with GitHub Actions.

**Basic Knowledge of the Following:**

**DevSecOps and CI/CD Pipelines:** Familiarity with GitHub Actions or other CI/CD tools.

**Kubernetes:** Understanding of basic Kubernetes concepts, including nodes, pods, services, and deployments.

**Docker:** Knowledge of Docker basics, including Dockerfile creation, image building, and pushing images to a container registry.

**JavaScript:** Basic understanding to implement modifications to the Infinite Mario game.

**Tools and Technologies Used**

Azure Kubernetes Service (AKS)
Docker and Docker Hub
SonarQube for SAST Scans
GitHub Actions for CI/CD
Trivy for Container Security
---

 **Pipeline Architecture**

The pipeline architecture integrates the following stages:

1. **Code Commit**: Push code changes to GitHub.
2. **Build & Test**: Run unit tests and static code analysis using SonarQube.
3. **Containerization**: Build and push Docker images to Docker Hub.
4. **Security Scanning**: Scan images with Trivy for vulnerabilities.
5. **Deployment**: Deploy to AKS using ArgoCD.

![Pipeline Architecture](path/to/your/image.png)  <!-- Replace with the path to your architecture diagram -->

---

 **Step-by-Step Implementation**
 Here's a focused step-by-step guide for creating an Azure account as the first step in your DevSecOps pipeline project:

---

**Step 1: Create an Azure Cloud Account**

**Objective**
To set up a free Azure cloud account for hosting resources required for your DevSecOps pipeline.

 **Instructions**

**1. Navigate to the Azure Free Account Page**
- Open your web browser and go to the [Azure Free Account](https://azure.microsoft.com/free/) page.

 **2. Start Free Trial**
- Click on the **Start free** button. This will direct you to the signup page.

 **3. Sign In or Create a Microsoft Account**
- If you already have a Microsoft account, sign in using your credentials.
- If you don’t have an account, click on **Create one** to set up a new Microsoft account.

**4. Fill Out Required Information**
- Complete the registration form with the following details:
  - **First Name**
  - **Last Name**
  - **Phone Number** (You may choose to receive a verification code via SMS or call)
  - **Email Address** (Use your Microsoft account email)
  - **Country/Region**

**5. Verify Your Identity**
- Depending on the method you selected, enter the verification code you received via SMS or voice call.
  
**6. Provide Payment Information**
- Enter your credit card details. **Note:** You won’t be charged during the free trial period, but Microsoft requires this information for verification purposes.

**7. Accept Terms and Conditions**
- Review and accept the terms and conditions by checking the box and clicking on **Sign up**.

 **8. Complete the Setup**
- After a brief setup process, you will receive a confirmation that your Azure account has been created.
- You will also be given a credit of $200 for the first 30 days to explore Azure services.

 **9. Access the Azure Portal**
- Click on **Go to the Azure Portal** to access your new Azure account dashboard.

For detailed information about free trail: Follow this link : [how-to-add-a-trial-subscription-to-your-azureaccount(https://techcommunity.microsoft.com/t5/startups-at-microsoft/how-to-add-a-trial-subscription-to-your-azure-account-step-by/ba-p/3792372)
 



This concludes Step 1 of setting up your DevSecOps pipeline. Once your Azure account is ready, you can proceed to the next steps in your project.

