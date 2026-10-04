# AWS Cloud Infrastructure Deployment

## 📌 Project Overview

This project demonstrates the deployment of a basic web server infrastructure on Amazon Web Services (AWS).

The infrastructure was designed using an AWS VPC with public and private subnets. An Ubuntu EC2 instance was deployed in the public subnet and configured with Nginx to serve a web page over HTTP.

The project focuses on understanding AWS networking, compute, security and basic web server deployment.

---

## 🏗️ Architecture

```text
                         Internet
                            │
                            ▼
                    Internet Gateway
                            │
                            ▼
                 VPC: 10.0.0.0/16
                            │
              ┌─────────────┴─────────────┐
              │                           │
              ▼                           ▼
       Public Subnet                Private Subnet
        10.0.1.0/24                 10.0.2.0/24
              │
              ▼
       Ubuntu EC2 Instance
       Private IP: 10.0.1.x
       Public IPv4: Assigned
              │
              ▼
          Nginx :80
              │
              ▼
       Web Page in Browser
```

---

## ☁️ AWS Services Used

* Amazon VPC
* Amazon EC2
* Amazon VPC Subnets
* Internet Gateway
* Route Tables
* Security Groups
* Ubuntu Server 24.04 LTS
* Nginx Web Server

---

## 🌐 Network Configuration

### VPC

* Name: `devops-project-vpc`
* CIDR: `10.0.0.0/16`

### Public Subnet

* Name: `public-subnet`
* CIDR: `10.0.1.0/24`
* Availability Zone: `ap-south-1a`

### Private Subnet

* Name: `private-subnet`
* CIDR: `10.0.2.0/24`
* Availability Zone: `ap-south-1a`

### Internet Gateway

* Name: `devops-project-igw`
* Attached to the project VPC

### Public Route Table

* Name: `public-route-table`
* Route:

  * `0.0.0.0/0 → Internet Gateway`
* Associated subnet:

  * `public-subnet`

---

## 🔐 Security Configuration

A Security Group named `web-server-sg` was created for the EC2 web server.

### Inbound Rules

| Protocol | Port | Source    | Purpose                      |
| -------- | ---: | --------- | ---------------------------- |
| SSH      |   22 | My IP     | Secure server administration |
| HTTP     |   80 | 0.0.0.0/0 | Web traffic                  |

Outbound traffic uses the default configuration.

---

## 🖥️ EC2 Configuration

* Instance Name: `devops-web-server`
* Operating System: Ubuntu Server 24.04 LTS
* Deployment: Public Subnet
* Public IPv4: Enabled
* SSH authentication: EC2 Key Pair
* Web Server: Nginx

The server was accessed remotely using SSH with the EC2 key pair.

---

## 🌍 Nginx Deployment

Nginx was installed on the Ubuntu EC2 instance using:

```bash
sudo apt update
sudo apt install nginx -y
```

The Nginx service was verified using:

```bash
sudo systemctl status nginx
```

The service was successfully running and the default Nginx webpage was accessed through the EC2 public IPv4 address.

---

## ✅ Verification

The deployment was verified by accessing the EC2 instance's public IP from a web browser.

The default Nginx welcome page was successfully displayed, confirming that:

* The EC2 instance was running.
* The instance had Internet connectivity.
* The Internet Gateway and route configuration were working.
* Security Group allowed HTTP traffic on port 80.
* Nginx was running successfully.

---

## 📸 Screenshots

### VPC
![VPC](vpc.png)

### Subnets
![Subnets](subnets.png)

### Internet Gateway
![Internet Gateway](internet-gateway.png)

### Route Table
![Route Table](route-table.png)

### Security Group
![Security Group](security-group.png)

### EC2 Instance
![EC2 Instance](ec2-instance.png)

### Nginx Web Page
![Nginx](nginx.png)

---

## 📚 What I Learned

Through this project, I gained practical understanding of:

* AWS VPC architecture
* Public and private subnets
* Internet Gateway
* Route tables and routing
* AWS Security Groups
* EC2 instance deployment
* SSH access to Linux servers
* Basic Linux server administration
* Nginx installation and service management
* Hosting a web server on AWS

---

## 🚀 Future Improvements

The infrastructure can be extended with:

* AWS IAM roles and policies
* S3 storage
* CloudWatch monitoring
* Application Load Balancer
* Auto Scaling
* Terraform Infrastructure as Code
* CI/CD using Jenkins and GitHub
* Docker-based application deployment
* Kubernetes deployment
