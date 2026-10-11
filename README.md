# Secure Linux Web Server on Azure ☁️🔐

 **⚠️ Important: Project Structure Update**

> This project was originally maintained as part of a combined Azure Enterprise Infrastructure repository containing both the Secure Linux Web Server project and the Identity & Access Security project. These projects have since been separated into independent repositories, each with its own documentation and learning objectives. Some resource names, folder names, and historical screenshots may still use the original V1/V2 labels because they were created before the separation. These labels are retained for historical accuracy and do not mean the projects are still combined.


A hands-on Microsoft Azure project focused on learning core cloud infrastructure concepts through the deployment of a secure Linux-based web server.

This project demonstrates fundamental cloud networking, Azure Virtual Machines, Linux administration, Network Security Groups (NSGs), SSH key authentication, and Nginx web hosting.

It was developed as a practical learning project for **Microsoft Azure Fundamentals (AZ-900)**.

---

## 🎯 Project Objective

The objective was to deploy a Linux virtual machine on Microsoft Azure and use it to host a static portfolio website.

The implementation covered:

- Organizing cloud resources with an Azure Resource Group
- Configuring an Azure Virtual Network and subnet
- Controlling inbound traffic with a Network Security Group
- Deploying an Ubuntu 24.04 LTS virtual machine
- Configuring SSH key-based authentication
- Installing and running the Nginx web server
- Hosting a static portfolio website accessible over HTTP

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

### Request Flow

```text
Internet
   ↓
Public IP Address
   ↓
Network Security Group
   ↓
Ubuntu Virtual Machine
   ↓
Nginx Web Server
   ↓
Portfolio Website
```

---

## ☁️ Azure Resources

| Resource | Purpose |
|---|---|
| Resource Group | Organizes the project's Azure resources |
| Virtual Network (VNet) | Provides a virtual network environment |
| Subnet | Provides a subnet for the virtual machine |
| Network Security Group (NSG) | Controls permitted inbound network traffic |
| Public IP Address | Enables external connectivity to the VM |
| Ubuntu Virtual Machine | Hosts the Linux web server |
| Nginx | Serves the static portfolio website |

---

## 🔐 Security Configuration

Security was considered at the network and authentication layers.

### SSH Key-Based Authentication

The virtual machine was configured to use an SSH key pair for administrative access instead of password-based SSH authentication.

This reduces reliance on password-based remote access. SSH private keys must be stored securely and must not be committed to the repository.

### Network Security Group

The NSG was configured to allow the inbound traffic required by the workload.

| Port | Protocol | Purpose |
|---:|---|---|
| 22 | TCP | SSH administration |
| 80 | TCP | HTTP web traffic |

**Security note:** The SSH rule should be restricted to trusted source IP addresses wherever possible. The actual deployed rule should be checked against the project's deployment notes and screenshots before claiming a specific source restriction.

### Network Isolation

The virtual machine was deployed inside an Azure Virtual Network and subnet. The NSG provided an additional layer of network traffic control.

This project demonstrates foundational cloud security practices. It is a learning environment, not a complete production-grade security architecture.

---

## 🌐 Web Server Deployment

Nginx was installed and configured on the Ubuntu virtual machine to serve the portfolio website.

The deployment process included:

1. Updating the Ubuntu package repository.
2. Installing Nginx.
3. Enabling and starting the Nginx service.
4. Verifying that the web server was listening on port 80.
5. Replacing the default Nginx landing page.
6. Deploying the static portfolio website.
7. Testing access through the VM's public IP address.

The website was served from:

```text
/var/www/html/index.html
```

---

## 🧪 Validation and Testing

The deployment was validated using Linux commands and browser-based testing.

### 1. Check the Nginx Service

```bash
sudo systemctl status nginx
```

### 2. Verify Port 80

```bash
sudo ss -tulpn | grep :80
```

### 3. Test the Web Server Locally

```bash
curl localhost
```

### 4. Test External Connectivity

The website was accessed through the virtual machine's public IP address over HTTP.

These checks helped verify the web server's service status, local response, and external accessibility.

---

## 📚 What I Learned

### Microsoft Azure

- Resource Groups and cloud resource organization
- Azure Virtual Networks and subnets
- Network Security Groups
- Public IP addressing
- Azure Virtual Machine deployment

### Linux Administration

- Basic Linux administration
- Package management with `apt`
- File management and permissions
- Service management with `systemctl`
- Nginx installation and configuration

### Networking

- TCP ports and inbound traffic
- SSH versus HTTP traffic
- Public IP connectivity
- Network Security Groups
- Basic network isolation

### Web Hosting

- Installing and managing Nginx
- Serving static websites
- Understanding the `/var/www/html` directory
- Testing web server connectivity

### Git and GitHub

- Maintaining a structured project repository
- Documenting infrastructure and deployment steps
- Using Git for version control
- Organizing project files and technical evidence

---

## 📂 Project Structure

```text
secure-linux-web-server-azure/
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

*The structure above reflects the intended repository layout. Verify the actual directory and file names in GitHub before publishing this section.*

---

## 🧠 Engineering Takeaway

A cloud-hosted website is more than a virtual machine running a web server. It depends on several connected infrastructure layers:

```text
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

Building this project helped me understand how these components work together to deliver a publicly accessible workload on Microsoft Azure.

It also provided practical experience with cloud resource organization, network configuration, Linux administration, remote access, and basic security controls.

---

## 🎓 Project Purpose

This repository is maintained as a **standalone AZ-900 learning project**.

It is separate from the Microsoft Entra ID and Azure RBAC project, which focuses on identity and access management concepts relevant to SC-900.

A future Azure Enterprise Infrastructure project may build on these foundational skills, but it will have its own repository, architecture, and cumulative implementation history.

---

## ⚠️ Project Status

**Status: Completed and documented**

The Azure environment was deployed, tested, and used to host the portfolio website.

The Azure resources may be deleted after testing to avoid unnecessary cloud charges. The source code, documentation, architecture files, and screenshots remain in the repository as a record of the implementation.

**Important:** The website may not remain publicly accessible if the VM and its associated resources have been deleted.

---

## 👨‍💻 Author

**Faizan Khan Khaleel**

BCA | Cloud Architecture & Cybersecurity

Areas explored through this project:

- ☁️ Cloud Engineering
- 🔐 Cybersecurity Fundamentals
- 🐧 Linux Administration
- 🌐 Computer Networking
- ⚙️ Infrastructure Engineering
