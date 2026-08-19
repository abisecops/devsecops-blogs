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

**Repository:** [Full Stack Blogging App](https://github.com/ougabriel/full-stack-blogging-app)

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

### Step 2: Setup Required Servers  (Jenkins, SonarQube, Nexus & Monitoring Tools)

In this step, we will deploy **two AWS EC2 instances** for **Nexus Repository** and **SonarQube**.

#### a. Log in to AWS Console

Log in to the AWS Management Console.

#### b. Navigate to EC2

In the AWS Console search bar, search for **EC2** and open the EC2 Dashboard.

#### c. Launch an Instance

Click **Launch instance**.

#### d. Configure Instance Details

Configure the instance as follows:

* **Name:** `Nexus-Server`
* **AMI:** Ubuntu Server
* **Instance type:** `t2.medium`
* **Key pair:** Select an existing key pair or create a new one.

For the second server, use:

* **Name:** `SonarQube-Server`
* **AMI:** Ubuntu Server
* **Instance type:** `t2.medium`

> **Note:** Ubuntu 20.04 is now an older release. For a new deployment, use an Ubuntu LTS version supported by the software you're installing, unless your project specifically requires Ubuntu 20.04.

#### e. Configure Network Settings

Select your preferred:

* **VPC**
* **Subnet**
* **Auto-assign Public IP:** Enable if you need direct Internet/SSH access.

Configure the Security Group with only the required ports.

For SSH:

```
SSH
TCP
22
Source: My IP
```

**Do not use `2000–11000` as the SSH source range.** If you meant a port range, that is also unnecessary and insecure. SSH should normally be restricted to your own public IP or VPN/bastion network.

For the application services, open only the ports actually required, for example:

| Server    | Service          | Port |
| --------- | ---------------- | ---: |
| Nexus     | Nexus Repository | 8081 |
| SonarQube | SonarQube Web UI | 9000 |
| SSH       | SSH              |   22 |

Ideally, restrict **8081** and **9000** to your trusted IP/network rather than opening them to `0.0.0.0/0`.

#### f. Configure Storage

Set the root EBS volume to at least:

```
20 GB
```

However, **20 GB may be insufficient for Nexus**, depending on how many artifacts/images you store. Nexus storage can grow quickly.

#### g. Number of Instances

You can either:

* Launch **2 instances at once**, or
* Launch them separately and give each a clear name.

For example:

```
Nexus-Server
SonarQube-Server
```

#### h. Launch Instances

Review the configuration and click **Launch instance**.

Wait until both instances show:

```
Instance state: Running
```

#### i. Connect to the Servers

Once the instances are running, select an instance and copy its **Public IPv4 address**.

Connect using SSH:

```bash
ssh -i your-key.pem ubuntu@<PUBLIC-IP>
```

For example:

```bash
ssh -i my-key.pem ubuntu@54.xx.xx.xx
```

Make sure your private key has the correct permissions:

```bash
chmod 400 my-key.pem
```

Then connect again:

```bash
ssh -i my-key.pem ubuntu@<PUBLIC-IP>
```

**Important:** Nexus and SonarQube can consume significant RAM. `t2.medium` has only **4 GiB RAM**, so monitor memory usage and consider a larger instance if you encounter Java out-of-memory or performance issues.
