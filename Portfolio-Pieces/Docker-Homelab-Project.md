# Dockerized Self-Hosted Infrastructure Lab

## Project Overview

The Dockerized Self-Hosted Infrastructure Lab was created to provide a centralized platform for learning Linux administration, networking, containerization, and security concepts.

The environment was designed to simulate a small business infrastructure while remaining inexpensive and easy to maintain.

---

# Objectives

The primary goals of the project were:

* Learn Docker and Docker Compose
* Deploy self-hosted services
* Improve Linux administration skills
* Practice network security concepts
* Build repeatable deployment procedures
* Document infrastructure and configurations

---

# Hardware Platform

## Server

Example platform:

```text
Raspberry Pi 4
8 GB RAM
2 TB SSD Storage
Ubuntu Server / Raspberry Pi OS
```

The platform was selected because of its:

* Low power consumption
* Low cost
* Reliability
* Community support

---

# Core Technologies

## Operating System

* Ubuntu Server
* Raspberry Pi OS

## Container Platform

* Docker
* Docker Compose

## Security Tools

* UFW
* Fail2Ban
* WireGuard

---

# Services Deployed

## WireGuard

Purpose:

Secure remote access to the environment.

Benefits:

* Encrypted communication
* Remote administration
* Reduced exposure of internal services

---

## Nextcloud

Purpose:

Private cloud storage and file synchronization.

Features:

* File sharing
* Mobile access
* Automatic uploads
* Web access

---

## Nginx Proxy Manager

Purpose:

Reverse proxy management.

Benefits:

* SSL certificate management
* Host-based routing
* Simplified web application publishing

---

## Pi-hole

Purpose:

Network-wide DNS filtering.

Benefits:

* Ad blocking
* DNS visibility
* Reduced malicious domain access

---

# Network Architecture

```text
Internet
    |
Router
    |
WireGuard VPN
    |
Docker Host
    |
+-------------------+
| Docker Containers |
+-------------------+
| Nextcloud         |
| Pi-hole           |
| Nginx Proxy Mgr   |
+-------------------+
```

---

# Security Controls

## Firewall

UFW configured to:

* Allow VPN traffic
* Restrict administrative access
* Block unnecessary inbound traffic

---

## SSH Hardening

Implemented controls:

* SSH key authentication
* Disabled root login
* Administrative account separation

---

## VPN Access

Internal services are intended to be accessed through WireGuard whenever possible.

Benefits:

* Reduced attack surface
* Secure remote administration
* Encrypted communications

---

# Example Docker Compose Workflow

Deploying services:

```bash
docker compose up -d
```

Viewing running containers:

```bash
docker ps
```

Viewing logs:

```bash
docker logs container_name
```

Stopping services:

```bash
docker compose down
```

---

# Challenges Encountered

During development several common issues were encountered:

* Container networking problems
* Firewall configuration issues
* DNS resolution issues
* Volume permission problems
* VPN routing challenges

These issues provided valuable troubleshooting experience and improved understanding of Linux networking concepts.

---

# Lessons Learned

Key skills developed through this project include:

* Linux administration
* Docker management
* Network troubleshooting
* VPN deployment
* Firewall configuration
* Infrastructure documentation
* Service monitoring

---

# Future Enhancements

Planned improvements include:

* Automated deployments
* Infrastructure as Code
* Monitoring and alerting
* Centralized logging
* Container vulnerability scanning
* Backup automation

---

# Results

The completed environment provides:

* Secure remote access
* Centralized file storage
* DNS filtering
* Reverse proxy functionality
* Practical learning opportunities

The project serves as both a functional home lab and a platform for continued learning and experimentation.

---

# Conclusion

This project demonstrates the use of Docker and open-source technologies to build a secure, flexible, and cost-effective infrastructure environment.

The knowledge gained through designing, deploying, securing, and maintaining the environment directly applies to real-world Linux administration, networking, and cybersecurity tasks.
