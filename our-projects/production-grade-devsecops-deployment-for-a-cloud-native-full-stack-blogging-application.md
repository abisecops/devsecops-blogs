---
description: >-
  This project implements a production level CI/CD and DevSecOps pipeline for
  deploying a full stack blogging application on AWS EKS using Jenkins, Docker,
  Nexus, SonarQube, Trivy and Prometheus.
---

# Production Grade DevSecOps Deployment for a Cloud Native Full Stack Blogging Application

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

### Tech Stack Used in This Project

**Tools Used:**

* **Jenkins:** For automating and managing the CI/CD pipeline.
* **SonarQube:** For code quality analysis and security checks.
* **Nexus:** For storing and managing application artifacts.
* **Trivy:** For identifying vulnerabilities in source files and Docker images.
* **Docker:** For containerizing the application.
* **Prometheus:** For collecting and monitoring system and application metrics.
* **Blackbox Exporter:** For monitoring application availability and endpoints.
* **Grafana:** For creating dashboards and visualizing monitoring data.
* **Kubernetes on AWS EKS:** For deploying and managing containerized applications.
* **Terraform:** For provisioning and managing AWS infrastructure.

### **Prerequisites:**

Before starting this project, you should have a basic understanding of the following:

* **CI/CD:** Basic understanding of Continuous Integration and Continuous Deployment.
* **AWS:** An AWS account with access to create and manage EC2 and EKS resources.
* **Git and GitHub:** Basic knowledge of Git and GitHub for source code management.
* **Linux:** Familiarity with basic Linux commands, terminal usage and SSH.
* **Jenkins, Docker and Kubernetes:** Basic understanding of setup, configuration and usage.

### Table of Contents

* **Step 1:** Set Up the Git Repository and Create a Security Token
* **Step 2:** Set Up the Required Servers for Jenkins, SonarQube, Nexus and Monitoring
* **Step 3:** Configure Jenkins, SonarQube and Nexus
* **Step 4:** Install Jenkins Plugins and Configure Nexus, Trivy, SonarQube and DockerHub
* **Step 5:** Create and Configure the Complete CI/CD Pipeline
* **Step 6:** Create the AWS EKS Cluster and Install AWS CLI, Kubectl and Terraform
* **Step 7:** Configure a Custom Domain for the Application
* **Step 8:** Set Up Application Monitoring with Prometheus, Blackbox Exporter and Grafana

This guide builds a secure delivery workflow from source control to Amazon EKS. It covers infrastructure provisioning, automated quality and security checks, container deployment, and production monitoring.

#### Steps 1: Set Up the Git Repository and Create a Security Token

#### a. Create the Git Repository

First, create a GitHub repository for the application. For production, it is recommended to keep the repository **private** for better security.

> For this project, I am keeping it **public** so you can easily access the source code and follow along.

**Repository:** [Full Stack Blogging App](https://github.com/ougabriel/full-stack-blogging-app?utm_source=chatgpt.com)

#### b. Create a Security Token

Next, create a **GitHub Personal Access Token (PAT)** to securely authenticate with your repository. It allows tools like Jenkins to access GitHub without exposing your actual password.

> **Tip:** Treat your token like a password and never share or commit it to your repository.

#### c. Install Git Bash and Clone the Repository

Install **Git Bash** on your local system. It makes it easy to manage the project, commit changes and push code to GitHub.

You can download Git from [Git Official Guide](https://github.com/git-guides/install-git).

Once Git Bash is installed, clone the project repository:

```bash
git clone https://github.com/ougabriel/full-stack-blogging-app.git
```

This will download the complete source code to your local system and prepare it for the next steps.

#### Steps 1: Set Up the Git Repository and Create a Security Token

#### a. Create the Git Repository

First, create a GitHub repository for the application. For production, it is recommended to keep the repository **private** for better security.

> For this project, I am keeping it **public** so you can easily access the source code and follow along.

**Repository:** [Full Stack Blogging App](https://github.com/ougabriel/full-stack-blogging-app?utm_source=chatgpt.com)

#### b. Create a Security Token

Next, create a **GitHub Personal Access Token (PAT)** to securely authenticate with your repository. It allows tools like Jenkins to access GitHub without exposing your actual password.

> **Tip:** Treat your token like a password and never share or commit it to your repository.

#### c. Install Git Bash and Clone the Repository

Install **Git Bash** on your local system. It makes it easy to manage the project, commit changes and push code to GitHub.

You can download Git from [Git Official Guide](https://github.com/git-guides/install-git).

Once Git Bash is installed, clone the project repository:

```bash
git clone https://github.com/ougabriel/full-stack-blogging-app.git
```

This will download the complete source code to your local system and prepare it for the next steps.

<figure><img src="../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>
