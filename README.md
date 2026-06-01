# NGINX Rotating Pages – Automated CI/CD Deployment on Amazon EC2

## Overview

This project demonstrates a complete CI/CD automation workflow using GitHub Actions and an Amazon Linux EC2 instance running NGINX.

The solution automatically deploys website updates whenever changes are pushed to the GitHub repository. Multiple static HTML pages are hosted on the EC2 instance, and NGINX serves them through a page-rotation mechanism.

---

## Architecture

```text
Developer
    │
    │ Git Push
    ▼
GitHub Repository
    │
    ▼
GitHub Actions
    │
    │ SSH Deployment
    ▼
Amazon Linux EC2
    │
    ├── Pull Latest Code
    ├── Update Website Files
    ├── Restart Rotation Service
    └── Reload NGINX
    │
    ▼
Live Website
```

---

## Project Goal

The objective of this project is to:

* Automate deployments using GitHub Actions
* Eliminate manual server updates
* Host static web pages on NGINX
* Automatically rotate displayed pages
* Demonstrate a simple CI/CD pipeline using AWS EC2

---

## Technologies Used

* GitHub
* GitHub Actions
* Amazon EC2
* Amazon Linux 2023
* NGINX
* Git
* SSH
* Bash Automation

---

## Deployment Workflow

Whenever a developer pushes changes to the main branch:

1. GitHub Actions is triggered automatically.
2. The workflow establishes a secure SSH connection to the EC2 instance.
3. The EC2 server pulls the latest code from GitHub.
4. Updated website files are copied to the NGINX web directory.
5. The page rotation process is restarted.
6. NGINX reloads its configuration.
7. Changes become available on the live website.

This entire process is fully automated and requires no manual login to the server.

---

## EC2 Server Responsibilities

The EC2 instance is responsible for:

* Hosting the website
* Running NGINX
* Pulling updates from GitHub
* Managing page rotation
* Serving content to end users

---

## GitHub Actions Responsibilities

GitHub Actions acts as the CI/CD engine by:

* Detecting repository changes
* Authenticating to EC2 using SSH
* Deploying updated files
* Triggering application restart procedures
* Ensuring the latest version is always deployed

---

## Security Configuration

The deployment process uses SSH key authentication.

Required GitHub Secrets:

| Secret Name | Description                         |
| ----------- | ----------------------------------- |
| EC2_SSH_KEY | Private SSH key used for deployment |
| EC2_HOST    | Public IP or DNS of EC2             |
| EC2_USER    | EC2 login user                      |

These secrets are securely stored in GitHub and are never exposed in the repository.

---

## Initial Infrastructure Setup

The following components must be configured once:

* Launch Amazon Linux EC2 instance
* Install NGINX
* Install Git
* Clone repository
* Configure SSH access
* Configure GitHub repository secrets
* Verify NGINX accessibility

After the initial setup, deployments become fully automated.

---

## Automated Deployment Lifecycle

```text
Code Change
      │
      ▼
Git Commit
      │
      ▼
Git Push
      │
      ▼
GitHub Actions Triggered
      │
      ▼
Connect to EC2
      │
      ▼
Download Latest Code
      │
      ▼
Update Website
      │
      ▼
Restart Rotation Process
      │
      ▼
Reload NGINX
      │
      ▼
Website Updated
```

---

## Benefits

* Fully automated deployments
* No manual server maintenance
* Faster release cycles
* Consistent deployment process
* Secure SSH-based access
* Simple architecture
* Cost-effective AWS hosting
* Easy to extend for future applications

---

## Use Cases

This project can be used as a reference for:

* CI/CD demonstrations
* AWS deployment learning
* NGINX hosting examples
* GitHub Actions automation
* Static website hosting
* DevOps beginner projects

---

## Future Enhancements

Potential improvements include:

* HTTPS using SSL certificates
* Custom domain integration
* Auto-scaling infrastructure
* Docker-based deployment
* Monitoring and logging
* AWS CodeDeploy integration
* Infrastructure as Code using Terraform

---

