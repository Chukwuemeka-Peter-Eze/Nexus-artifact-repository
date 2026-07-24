# Nexus Repository Manager Installation Guide (AWS)

## Overview

This document describes the complete installation process for deploying Nexus Repository Manager on an AWS EC2 instance running Ubuntu Linux.

The deployment creates a centralized artifact repository capable of storing, managing, and distributing software packages generated during the software development lifecycle.

This guide documents the practical implementation performed during this project.

---

# Prerequisites

Before beginning the installation, ensure the following requirements are met.

## AWS Resources

- AWS Account
- EC2 Instance
- Security Group
- SSH Key Pair
- Public IP Address

---

## Operating System

- Ubuntu Linux

---

## Software Requirements

- Java Runtime Environment (OpenJDK)
- wget
- tar
- SSH Client

---

# Architecture

```text
Developer

↓

SSH

↓

AWS EC2

↓

Ubuntu

↓

Java Runtime

↓

Nexus Repository Manager

↓

Repositories

↓

Blob Store
```

---

# Step 1 — Launch AWS EC2 Instance

Provision an Ubuntu EC2 instance with sufficient CPU, memory, and storage for Nexus Repository Manager.

Recommended specifications:

| Resource | Recommendation |
|-----------|----------------|
| Instance | t3.medium or equivalent |
| Storage | 20 GB+ |
| OS | Ubuntu |
| Public IP | Enabled |

---

> Insert Screenshot Here

```text
screenshots/01-ec2-instance.png
```

---

# Step 2 — Configure Security Group

Allow the required inbound traffic.

| Port | Purpose |
|------|---------|
| 22 | SSH |
| 8081 | Nexus Web Interface |

---

> Insert Screenshot Here

```text
screenshots/02-security-group.png
```

---

# Step 3 — Connect Using SSH

Connect securely to the EC2 instance.

> Insert Screenshot Here

```text
screenshots/03-ssh.png
```

---

# Step 4 — Install Java

Nexus Repository Manager requires a Java Runtime Environment before installation.

Verify that Java has been installed successfully.

---

> Insert Screenshot Here

```text
screenshots/04-java-installed.png
```

---

# Step 5 — Download Nexus Repository Manager

Download the Nexus installation package onto the EC2 instance.

---

> Insert Screenshot Here

```text
screenshots/05-download.png
```

---

# Step 6 — Extract Installation Package

Extract the downloaded archive.

---

> Insert Screenshot Here

```text
screenshots/06-extract.png
```

---

# Step 7 — Create Dedicated Nexus User

Create a non-root Linux user to own and run the Nexus service.

Using a dedicated service account improves security and follows Linux administration best practices.

---

> Insert Screenshot Here

```text
screenshots/07-user-created.png
```

---

# Step 8 — Configure File Permissions

Assign ownership of the Nexus installation directory and working directory to the Nexus user.

This ensures the application can read, write, and manage its files without elevated privileges.

---

> Insert Screenshot Here

```text
screenshots/08-permissions.png
```

---

# Step 9 — Configure Nexus Runtime

Update the Nexus runtime configuration so that the service starts using the dedicated Nexus user.

---

> Insert Screenshot Here

```text
screenshots/09-runtime-config.png
```

---

# Step 10 — Start Nexus Repository Manager

Start the Nexus service.

After startup, verify that the process is running correctly.

---

> Insert Screenshot Here

```text
screenshots/10-start-service.png
```

---

# Step 11 — Verify Running Process

Confirm that the Nexus service is active before attempting browser access.

---

> Insert Screenshot Here

```text
screenshots/11-process-verification.png
```

---

# Step 12 — Access the Web Interface

Open the Nexus web interface using the EC2 public IP address and the configured service port.

Verify that the login page loads successfully.

---

> Insert Screenshot Here

```text
screenshots/12-login-page.png
```

---

# Installation Validation Checklist

Use this checklist to verify a successful deployment.

- EC2 instance running
- Security Group configured
- SSH access confirmed
- Java installed
- Nexus downloaded
- Package extracted
- Dedicated Nexus user created
- Permissions configured
- Runtime configuration completed
- Nexus service started
- Web interface accessible
- Initial login successful

---

# Common Installation Issues

| Issue | Possible Cause | Resolution |
|-------|----------------|------------|
| Nexus does not start | Incorrect permissions | Verify directory ownership |
| Login page unavailable | Port 8081 blocked | Review Security Group rules |
| Java errors | Missing or incompatible runtime | Confirm Java installation |
| Service exits unexpectedly | Runtime configuration issue | Validate Nexus configuration |

---

# Security Recommendations

- Run Nexus using a dedicated Linux user.
- Limit inbound network access to required ports.
- Protect administrative credentials.
- Regularly update the operating system.
- Monitor storage utilization and system logs.
- Apply the principle of least privilege when creating Nexus users.

---

# Outcome

At the end of this installation, the Nexus Repository Manager was successfully deployed on an AWS EC2 instance and was ready for repository creation, artifact publishing, API integration, Blob Store configuration, and lifecycle management through Cleanup Policies.
