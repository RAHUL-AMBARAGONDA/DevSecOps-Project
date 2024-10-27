# End-to-End DevSecOps Pipeline for Super Mario Game 

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

**Step-by-Step Guide to Creating the Kubernetes Cluster in Azure**

1. Access the Kubernetes Cluster Creation Wizard in Azure
Log in to your Azure portal at portal.azure.com.

2. In the search bar at the top of the portal, type Kubernetes services and select it from the list of services.
Click on + Create to start the Kubernetes cluster creation process.

3. Configure Basic Cluster Settings
   
Under the Basics tab:

**Subscription:** Select Free Trial to use Azure’s free resources.

**Resource Group:** Select or create demo-resource-group.

**Cluster Preset Configuration:** Choose Dev/Test. This preset is optimized for demonstration purposes and is cost-effective.

**Kubernetes Cluster Name:** Enter demoKubernetesCluster.

**Region:** Select East US.

**Availability Zones:** Set to None for this demo configuration.

**AKS Pricing Tier:** Select Free to keep the cluster within the free tier options.

**3. Configure Kubernetes Version and Upgrade Settings**

**Kubernetes Version:** Select 1.27.7 (the default version available).

**Automatic Upgrade:** Set to Disabled to manually control version upgrades.

**4. Set Authentication and Authorization Options**

**Authentication Method:** Choose Local Accounts with Kubernetes RBAC to enable Role-Based Access Control for added security.

**5. Configure Node Security and Scheduling**

**Node Security Channel Type:** Set Node Image as the security channel type.

**Scheduler Option:** Choose No Schedule to prevent unnecessary load on nodes reserved for security tasks.

**Step 3: Configuring Node Pools for Kubernetes Cluster**

In this step, we will configure the node pools for our Kubernetes cluster to define the resource allocation and scaling behavior for the nodes that make up the cluster.

**Understanding Node Pool Quotas and Limitations (Free Tier)**

In the Free Tier of Azure, there is a quota limit of 4 node pools with a total capacity of 4 vCPUs. This means that:

If you use two nodes, each can have 2 vCPUs.

This limit is ideal for lightweight applications or demos, like this DevSecOps project.

**Note: If you upgrade to a paid tier, these limitations can be lifted, allowing for additional CPU resources and node pools.**

**Node Pool Configuration Steps**

Delete the Default System Node Pool (Optional for Paid Tier)

Since the Free Tier has limited capacity, delete the default system node pool created by Azure.
This ensures that your cluster’s quota is optimized for the nodes you configure manually.
Add a New Node Pool (System Node)

**Configure the node pool settings for your system node as follows:**

**Node Pool Name:** demosysnode

**Mode:** Select System to designate this as the main node pool handling essential cluster operations.

**OS SKU:** Choose Azure Linux (Linux is required for system node pools).

**Availability Zones:** Select None.

**Enable Azure Spot Instances:** Leave Disabled (Spot instances are not compatible with system node pools).

**Node Size:** Standard D2pds v6 2 vcpus, 8 GiB memory

**Scale Method:** Choose Manual or Autoscale (recommended for automatic scaling).

**Node Count:** Set to 1 node.

**Max Pods per Node:** Set to 30 (can be adjusted between 30 - 250).

**Enable Public IP per Node:** Leave Disabled (optional for this demo).

**Add a New Node Pool (User Node)**

We will now add a User Node pool with similar settings to support the application workloads in the cluster.

Configure the User Node settings similarly, making sure it is designated for workload handling.

**Step 4: Configuring the User Node Pool in Kubernetes Cluster**

With the system node pool configured, we’ll now add a user node pool that will manage our application workloads within the Kubernetes cluster. This setup allows us to distribute the cluster's responsibilities, separating system processes from user-defined workloads.

**User Node Pool Configuration**

**Configure the settings for the User Node Pool as follows:**

**Node Pool Name:** Set as demousermode.

**Mode:** Select User.

This designation focuses on handling application workloads, leaving essential cluster processes to the system node pool.

**OS SKU:** Choose Azure Linux for consistency, though Ubuntu Linux and Windows versions (2022 or 2019) are also available.

**Availability Zones:** Select Zone 1 to ensure the user node pool resides in the same geographic zone for optimized latency and failover.

**Enable Azure Spot Instances:** Leave Disabled.

Spot instances are cost-effective but can lead to interruptions, making them better suited for non-critical tasks.

**Node Size:** Set to Standard D2pds v5 (2 vCPUs, 8 GiB memory).

This configuration provides more memory, useful for handling multiple application containers.

**Scale Method:** Choose Autoscale (recommended).

Autoscaling dynamically adjusts the node count based on workload requirements, ensuring optimal resource usage without manual intervention.

**Node Count:** Set the initial count to 3 nodes.

This configuration allows for better load distribution and redundancy within the user node pool.

Optional Settings

Max Pods per Node: Set to 30 (adjustable between 10 - 250).

Enable Public IP per Node: Leave Disabled (recommended unless each node requires individual external access).


