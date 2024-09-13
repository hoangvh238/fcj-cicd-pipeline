---
title : "Designing CI/CD Solution"
date :  "`r Sys.Date()`" 
weight : 5 
chapter : false
pre : " <b> 2.1. </b> "
---

## Designing CI/CD Solution

![daily-dev.gif](../daily-dev.gif)

Architecture Overview for CI/CD Pipeline with Jenkins, Docker Hub, and SonarQube.

The diagram illustrates a CI/CD pipeline designed to deploy a **Razor Pages** web application hosted on an **EC2 instance** within AWS. This setup leverages **Jenkins** for continuous integration, **Docker Hub** for container image management, and **SonarQube** for code quality and security analysis.

### Pipeline Phases:

1. **Build**: Jenkins pulls the latest code from the **GitHub** repository, runs tests, and builds the project. During this process, SonarQube is integrated to analyze the codebase for potential quality and security issues.
2. **Push to Docker Hub**: Once the build is complete, Jenkins creates a Docker image from the application and pushes it to **Docker Hub**. This image contains the application and its dependencies, making it ready for deployment.
3. **Deploy**: The newly created Docker image is pulled from Docker Hub and deployed to an **EC2 instance** in a **public subnet**. This EC2 instance runs the Razor Pages application, and it is accessible over the Internet via **port 80**.

### Job Execution Environment:

- **Jenkins**: Hosted on an EC2 instance, Jenkins automates the build, test, and deploy phases. It triggers the SonarQube analysis during the build process and interacts with Docker Hub to manage container images.
- **SonarQube**: Deployed on a separate EC2 instance, SonarQube performs static code analysis during the Jenkins build phase, ensuring code quality and identifying any security vulnerabilities before the application is deployed.
- **Amazon RDS (Relational Database Service)**: The application interacts with a database hosted on **RDS**, located in a private subnet to enhance security. This private database is only accessible by the EC2 instance hosting the web application.

### How it Works:

1. **Code Commit**: A developer commits code changes to the **GitHub repository**.
2. **Jenkins Pipeline Trigger**: Jenkins detects the new commit and triggers the CI/CD pipeline defined in the Jenkins job configuration.
3. **Code Analysis and Build**: Jenkins pulls the code, performs a static analysis using SonarQube, and runs tests. Once successful, Jenkins builds the project and creates a Docker image.
4. **Image Push to Docker Hub**: The built Docker image is pushed to Docker Hub, where it is stored and versioned.
5. **Deployment to EC2**: Jenkins shh to EC2 and will pull  and run the latest Docker image from .The EC2 instance is connected to the Internet via an **Internet Gateway**, making the hosted web application accessible via **port 80**.
6. **Database Interaction**: The web application on EC2 interacts with the **RDS database** in the private subnet, ensuring data is securely managed without direct exposure to the public Internet.
7. **User Access**: End users access the web application over the Internet through the EC2 instance running in the public subnet.

---

### Key Components in the Architecture:

- **EC2 (Elastic Compute Cloud)**: Hosts the Razor Pages web app and Jenkins.
- **Docker Hub**: Stores the Docker image created from the application.
- **Jenkins**: Manages the CI/CD pipeline, integrating with GitHub, Docker Hub, and SonarQube.
- **SonarQube**: Performs code quality checks to ensure reliable and secure deployments.
- **RDS**: Provides a private database that the application can securely access.

By implementing this architecture, you ensure a seamless and automated process for building, testing, and deploying your web application, all while maintaining code quality and security through continuous integration and continuous deployment.