# Secure Linux Web Server on Azure ☁️🔐

A hands-on cloud infrastructure project that demonstrates how to deploy and secure a Linux-based web server on Microsoft Azure.

The project focuses on the fundamentals of cloud networking, Linux administration, network security, SSH-based authentication, and web server deployment.

---

## 🎯 Project Objective

The goal of this project was to deploy a secure Linux web server on Microsoft Azure and host a static portfolio website.

The infrastructure was designed to provide:

- A dedicated Azure environment for the workload
- Network isolation using an Azure Virtual Network
- Controlled inbound traffic using a Network Security Group
- Secure SSH access using an SSH key pair
- A Linux-based web server using Ubuntu 24.04 LTS
- Nginx for serving the website
- Public HTTP access to the hosted portfolio

---

## 🏗️ Architecture

```text
                         Internet
                            │
                            ▼
                     Public IP Address
                            │
                            ▼
                  Network Security Group
                     ┌──────┴──────┐
                     │             │
                  SSH :22       HTTP :80
                     │             │
                     └──────┬──────┘
                            ▼
                    Azure Virtual Network
                            │
                         Subnet
                            │
                            ▼
                    Ubuntu 24.04 LTS VM
                            │
                            ▼
                          Nginx
                            │
                            ▼
                  Static Portfolio Website
```


## Request Flow
```
Internet
   ↓
Public IP
   ↓
Azure NSG
   ↓
Ubuntu VM
   ↓
Nginx
   ↓
Portfolio Website
```


## ☁️ Azure Resources

The deployment consisted of the following Azure resources:

Resource	Purpose
Resource Group	Organizes the project resources
Virtual Network	Provides network isolation
Subnet	Hosts the virtual machine
Network Security Group	Controls inbound network traffic
Public IP Address	Provides external access to the web server
Ubuntu VM	Hosts the web server
Nginx	Serves the portfolio website


## 🔐 Security Configuration

Security was considered at the network and authentication layers.

### SSH Key Authentication

The virtual machine was configured to use an SSH key pair rather than password-based authentication.

This provides a stronger authentication mechanism for administrative access.

### Network Security Group
```
Inbound traffic was restricted to the ports required by the workload:
| Port | Protocol | Purpose            |
| ---: | -------- | ------------------ |
|   22 | TCP      | SSH administration |
|   80 | TCP      | HTTP web traffic   |
```
No unnecessary inbound application ports were opened.

### Network Isolation

The VM was deployed inside an Azure Virtual Network and subnet, with the Network Security Group controlling permitted inbound traffic.


## 🌐 Web Server Deployment

Nginx was installed and configured on the Ubuntu virtual machine.

The deployment process included:

Updating the Ubuntu package repository
Installing Nginx
Enabling the Nginx service
Starting the service
Verifying that Nginx was listening on port 80
Replacing the default Nginx page
Deploying the portfolio website
Testing the website through the VM's public IP

The website was served from:
/var/www/html/index.html


## 🧪 Validation & Testing

The deployment was validated at multiple layers.

### Nginx Service
sudo systemctl status nginx
### Port Verification
sudo ss -tulpn | grep :80
### Local Web Server Test
curl localhost
### External Web Test
The website was accessed through the VM's public IP address using HTTP.


## 📚 What I Learned
### Azure
Resource Groups and resource organization
Virtual Networks and Subnets
Network Security Groups
Public vs private IP addressing
Azure VM deployment
### Linux
Basic Linux administration
Package management with apt
File management and permissions
Service management with systemctl
Nginx configuration
### Networking
TCP ports and inbound traffic
SSH vs HTTP traffic
Network Security Groups
Public IP connectivity
Basic network isolation
### Web Hosting
Installing and managing Nginx
Serving static websites
Understanding /var/www/html
Testing web server connectivity
### Git & GitHub
Maintaining a structured project repository
Documenting infrastructure
Using Git for version control
Keeping development work organized locally before pushing to GitHub


## 📂 Project Structure
```
V1-Secure-Linux-Web-Server/
│
├── Portfolio/
│   └── index.html
│
├── docs/
│   ├── architecture/
│   │   ├── v1-architecture.md
│   │   └── v1-architecture.png
│   │
│   ├── notes/
│   │   ├── commands.md
│   │   ├── deployment-steps.md
│   │   ├── lessons-learned.md
│   │   └── troubleshooting.md
│   │
│   └── screenshots/
│
└── README.md
```


## 🧠 Engineering Takeaway

This project establishes the foundation for the larger Azure Enterprise Infrastructure project.

Rather than treating cloud infrastructure as simply "create a VM and run a website", this version introduces the fundamental layers involved in a real cloud workload:
```
Application
    ↓
Web Server
    ↓
Operating System
    ↓
Virtual Machine
    ↓
Network
    ↓
Security Controls
    ↓
Cloud Infrastructure
```
Future versions build on these foundations by introducing stronger identity management, least-privilege access, infrastructure as code, security monitoring, automation, and enterprise architecture.


## 🚀 Project Evolution

This project is the first stage of a larger evolving Azure infrastructure project.

Version          Focus
V1	            Secure Linux Web Server
V2	            Identity & Access Security
V3	            Cloud Security & Hardening
V4	            Operations & Security Monitoring
V5	            Enterprise Cloud Architecture

Each version is designed as an independent implementation so that the infrastructure can be deployed, tested, documented, and evaluated without requiring the previous Azure environment to remain running.


### ⚠️ Project Status

### Completed ✅

The V1 environment was successfully deployed, tested, documented, and used to host the portfolio website.

The Azure resources can be removed after testing to avoid unnecessary cloud costs while the project documentation and GitHub repository remain as the permanent record of the implementation.


## 👨‍💻 Author

### Faizan Khan Khaleel

BCA | Cloud Architecture & Cybersecurity

This project is part of my hands-on journey into:

☁️ Cloud Engineering
🔐 Cybersecurity
🐧 Linux
🌐 Networking
⚙️ Infrastructure Engineering


### One small improvement I deliberately made

I **didn't claim V1 is an "enterprise-grade secure architecture."** That would be résumé-flavored fiction. The actual project is a solid **foundation-level secure Linux web server**, and the repository itself documents that exact scope. :contentReference[oaicite:1]{index=1}

The README also clearly positions V1 as the foundation for the later versions, which makes the repository's evolution much easier for a recruiter to understand.
