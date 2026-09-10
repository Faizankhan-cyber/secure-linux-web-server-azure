# Azure Enterprise Infrastructure - Version 1 Deployment

## Objective

Deploy a secure Linux web server on Microsoft Azure and host a personal portfolio website.

---

## Resources Created

- Resource Group
- Virtual Network (VNet)
- Subnet
- Network Security Group (NSG)
- Public IP Address
- Ubuntu 24.04 LTS Virtual Machine

---

## VM Configuration

- Operating System: Ubuntu Server 24.04 LTS
- Authentication: SSH Key Pair
- Size: Standard B1s

---

## Network Configuration

Allowed inbound ports:

- SSH (22)
- HTTP (80)

---

## Web Server

Installed Nginx and configured it to start automatically.

Verified installation by accessing:

http://<Public-IP>

---

## Website Deployment

Uploaded a single-file HTML portfolio website.

Copied the website to:

/var/www/html/index.html

Verified deployment using the VM public IP.

---

## Status

✅ Version 1 completed successfully.