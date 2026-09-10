# Version 1 Architecture

## Overview

Version 1 deploys a secure Linux web server on Microsoft Azure to host a static portfolio website.

## Components

- Resource Group
- Virtual Network
- Subnet
- Network Security Group
- Public IP Address
- Ubuntu Virtual Machine
- Nginx Web Server
- Static Portfolio Website

## Request Flow

Internet
    ↓
Public IP
    ↓
Network Security Group (Port 80)
    ↓
Ubuntu Virtual Machine
    ↓
Nginx
    ↓
Portfolio Website

## Security

- SSH restricted to port 22
- HTTP allowed on port 80
- Authentication using SSH key pair
- Linux firewall inactive (Azure NSG used)