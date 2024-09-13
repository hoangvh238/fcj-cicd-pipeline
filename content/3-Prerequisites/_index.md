---
title : "Prerequisites"
date :  "`r Sys.Date()`" 
weight : 7 
chapter : false
pre : " <b> 3. </b> "
---


### 

### 1. **Virtual Private Cloud (VPC)**

You will need a **Virtual Private Cloud (VPC)** to isolate and secure your resources in AWS. Placing services like **EC2** instances, **RDS** databases, and other services inside a VPC ensures network-level security and allows you to define custom **Security Groups (SG)** and **Network Access Control Lists (NACL)** for fine-tuned access control.

- **Public Subnet**: Hosts the **public-app** on an EC2 instance, which is accessible via the internet through HTTP/HTTPS.
- **Private Subnet**: Hosts the **private-db** (RDS) that is isolated from public access. It can only communicate with resources inside the VPC, such as the EC2 instance.
- **Security Groups**: These act as virtual firewalls, controlling the traffic that flows to and from your EC2 instances, RDS databases, and other services.

**Best Practice**: It is recommended to create a separate VPC for this project instead of using the default VPC to ensure better control over networking and security.

### 2. **DockerHub Account**

You need a **DockerHub** account to host your container images. Once the code is built by Jenkins, the resulting Docker image will be pushed to **DockerHub** for versioning and reuse.

- **CI/CD Pipeline**: Jenkins will build Docker images based on the source code pulled from GitHub, and push the images to DockerHub for storage and deployment.

**Link Refer** : [Docker Hub](https://hub.docker.com/)

### 3. **GitHub Repository**

Ensure you have a **GitHub repository** set up to host the source code for your application. The CI/CD pipeline will pull the latest version of the code from this repository whenever a commit or pull request is made.

**You can use my template repo** : https://github.com/hoangvh238/Blog-razor-page

### 

[3.1. Create VPC](./3.1-CreateVPC/3.1-CreateVPC/_index.md)

[3.2 Create Dockerfile ](3.2-Create%20Dockerfile/_index.md)