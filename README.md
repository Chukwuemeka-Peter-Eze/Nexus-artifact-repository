# Nexus Artifact Repository on AWS

<p align="center">

![AWS](https://img.shields.io/badge/Cloud-AWS-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white)
![Ubuntu](https://img.shields.io/badge/OS-Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-Administration-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Java](https://img.shields.io/badge/Java-Runtime-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Nexus Repository](https://img.shields.io/badge/Artifact-Nexus%20Repository-1B1C30?style=for-the-badge)
![Maven](https://img.shields.io/badge/Maven-Build%20Tool-C71A36?style=for-the-badge&logo=apachemaven&logoColor=white)
![Gradle](https://img.shields.io/badge/Gradle-Build%20Tool-02303A?style=for-the-badge&logo=gradle&logoColor=white)
![REST API](https://img.shields.io/badge/API-REST-009688?style=for-the-badge)

</p>

---

# Repository Banner

> **Replace the image below with your custom project banner.**

```text
images/banner.png
```

---

# Table of Contents

- Project Overview
- Objectives
- Key Features
- Technology Stack
- Project Architecture
- Project Workflow
- Repository Structure
- Documentation
- Screenshots
- Demo Video
- Skills Demonstrated
- Lessons Learned
- Future Improvements
- License

---

# Project Overview

This repository documents the end-to-end deployment, configuration, and administration of **Nexus Repository Manager** on an **AWS EC2** instance.

The project demonstrates how a centralized artifact repository can be deployed to manage software packages, organize repositories, store build artifacts, expose REST APIs, manage storage through Blob Stores, and automate artifact lifecycle management with Cleanup Policies.

Rather than focusing only on installation, this repository captures the complete engineering process—from infrastructure provisioning and system configuration to repository administration, operational validation, troubleshooting, and technical documentation.

The implementation is supported with architecture diagrams, screenshots, command references, demonstration videos, and detailed implementation guides to provide a reproducible reference for similar deployments.

---

# Project Objectives

The primary objectives of this project were to:

- Deploy Nexus Repository Manager on AWS EC2.
- Configure the required runtime environment.
- Create and manage hosted repositories.
- Explore proxy and group repositories.
- Understand Blob Store architecture.
- Configure Cleanup Policies.
- Explore the Nexus REST API.
- Publish and manage software artifacts.
- Document the implementation using engineering best practices.
- Produce a reusable deployment reference for future projects.

---

# Key Features

This repository includes:

- AWS-based deployment of Nexus Repository Manager
- Linux server administration
- Java runtime configuration
- Repository creation and management
- Hosted, Proxy, and Group repository exploration
- Blob Store configuration
- Cleanup Policy implementation
- Artifact publishing workflows
- REST API exploration
- Operational troubleshooting
- Command reference documentation
- Architecture diagrams
- Practical implementation screenshots
- Project walkthrough video

---

# Technology Stack

| Category | Technology |
|-----------|------------|
| Cloud Platform | AWS EC2 |
| Operating System | Ubuntu Linux |
| Artifact Repository | Nexus Repository Manager |
| Runtime | Java |
| Build Tools | Maven, Gradle |
| API | Nexus REST API |
| Shell | Bash |
| Documentation | Markdown |
| Architecture | draw.io |
| Version Control | Git & GitHub |

---

# Repository Highlights

| Area | Implementation |
|------|----------------|
| Infrastructure | AWS EC2 Deployment |
| Artifact Storage | Nexus Repository Manager |
| Repository Types | Hosted, Proxy, Group |
| Storage Management | Blob Stores |
| Lifecycle Management | Cleanup Policies |
| API Integration | REST API |
| Documentation | Comprehensive Markdown Guides |
| Troubleshooting | Operational Runbooks |
| Evidence | Screenshots & Video Demonstration |

---

# Why This Project Matters

Artifact repositories are a critical component of modern software delivery pipelines.

By introducing a centralized location for storing, versioning, and distributing software artifacts, organizations can improve build consistency, simplify dependency management, strengthen governance, and support scalable CI/CD workflows.

This project demonstrates the foundational practices involved in deploying and operating an artifact repository in a cloud environment while documenting the implementation in a way that is reproducible and maintainable.

---

# Project Architecture

The diagram below illustrates the high-level architecture implemented during this project.

> **Replace the placeholder below with your exported draw.io architecture diagram.**

```text
architecture/aws-nexus-architecture.png
```

---

# High-Level Architecture

```text
                         Developer

                              │

                              ▼

                    SSH / Web Browser

                              │

                              ▼

                      AWS EC2 Instance

                              │

                              ▼

                     Ubuntu Linux Server

                              │

                              ▼

                Nexus Repository Manager

          ┌──────────────┼──────────────┐
          │              │              │
          ▼              ▼              ▼

   Hosted Repository  Proxy Repository  Group Repository

          │
          ▼

      Blob Store

          │
          ▼

   Physical Storage

          │
          ▼

 Maven / Gradle Artifacts
```

---

# Project Workflow

The following workflow summarizes the implementation completed during this project.

```text
Launch AWS EC2 Instance

↓

Configure Security Groups

↓

Connect via SSH

↓

Install Java Runtime

↓

Download Nexus Repository Manager

↓

Configure Nexus

↓

Start Nexus Service

↓

Access Web Interface

↓

Create Repositories

↓

Configure Blob Store

↓

Configure Cleanup Policies

↓

Explore REST API

↓

Publish Artifacts

↓

Validate Deployment

↓

Document Implementation
```

---

# Repository Structure

```text
Nexus-artifact-repository/

│
├── README.md
├── LICENSE
├── .gitignore
│
├── architecture/
│   ├── aws-nexus-architecture.drawio
│   ├── aws-nexus-architecture.png
│   └── workflow.drawio
│
├── docs/
│   ├── installation.md
│   ├── repository-management.md
│   ├── api-reference.md
│   ├── blob-store-cleanup-policy.md
│   ├── troubleshooting.md
│   ├── commands.md
│   ├── lessons-learned.md
│   └── project-summary.md
│
├── images/
│   ├── banner.png
│   └── architecture-overview.png
│
├── screenshots/
│   ├── 01-ec2-instance.png
│   ├── 02-security-group.png
│   ├── 03-ssh-access.png
│   ├── ...
│   └── final-dashboard.png
│
├── scripts/
│   ├── install-nexus.sh
│   ├── start-nexus.sh
│   ├── stop-nexus.sh
│   └── backup.sh
│
└── videos/
    └── demo.mp4
```

---

# Screenshot Gallery

The following screenshots document the implementation process from infrastructure provisioning through repository administration.

| Phase | Screenshot |
|--------|------------|
| AWS EC2 Instance | *(Insert Screenshot)* |
| Security Group Configuration | *(Insert Screenshot)* |
| SSH Connection | *(Insert Screenshot)* |
| Java Installation | *(Insert Screenshot)* |
| Nexus Download | *(Insert Screenshot)* |
| Nexus Dashboard | *(Insert Screenshot)* |
| Hosted Repository | *(Insert Screenshot)* |
| Blob Store Configuration | *(Insert Screenshot)* |
| Cleanup Policy | *(Insert Screenshot)* |
| REST API Demonstration | *(Insert Screenshot)* |
| Artifact Publishing | *(Insert Screenshot)* |
| Final Working Environment | *(Insert Screenshot)* |

> Replace each placeholder with the corresponding screenshot from the `screenshots/` directory.

---

# Project Demonstration

A walkthrough video accompanies this repository and demonstrates the deployment, configuration, and validation of the Nexus Repository Manager environment.

Suggested topics to cover in the video:

- Project introduction
- AWS infrastructure overview
- Nexus installation
- Repository creation
- Blob Store configuration
- Cleanup Policy configuration
- REST API exploration
- Artifact publishing
- Repository validation
- Lessons learned

> **Video Placeholder**

```text
videos/demo.mp4
```

If you upload the video to YouTube or another platform, you can replace the placeholder with the public link.

---

# Documentation Hub

Detailed implementation guides are available in the `docs/` directory.

| Document | Description |
|----------|-------------|
| `installation.md` | Complete installation and configuration guide |
| `repository-management.md` | Hosted, Proxy, and Group repository management |
| `api-reference.md` | REST API exploration and usage |
| `blob-store-cleanup-policy.md` | Blob Stores, Components, Assets, and Cleanup Policies |
| `troubleshooting.md` | Common issues and operational troubleshooting |
| `commands.md` | Command reference and administration cheatsheet |
| `lessons-learned.md` | Technical insights and engineering takeaways |
| `project-summary.md` | Executive summary of the implementation |

---

# Skills Demonstrated

This project provided hands-on experience across multiple areas of DevOps, cloud infrastructure, Linux administration, and software artifact management.

## Cloud Infrastructure

- Provisioning and managing AWS EC2 instances
- Configuring Security Groups for controlled network access
- Remote server administration using SSH
- Infrastructure validation and monitoring

---

## Linux System Administration

- Linux user and permission management
- File and directory ownership configuration
- Service management
- Log inspection and troubleshooting
- Process monitoring
- Basic network diagnostics

---

## Artifact Repository Management

- Nexus Repository Manager installation
- Repository administration
- Hosted repository configuration
- Proxy repository exploration
- Group repository exploration
- Repository lifecycle management

---

## Software Package Management

- Maven artifact publishing
- Gradle artifact publishing
- Artifact version management
- Repository organization
- Dependency management concepts

---

## Storage Management

- Blob Store configuration
- Components and Assets
- Cleanup Policies
- Cleanup Tasks
- Repository storage optimization

---

## REST API Integration

- Repository API exploration
- Repository information retrieval
- Asset management
- API authentication
- Administrative automation concepts

---

## Documentation

- Technical documentation
- Architecture diagrams
- Operational runbooks
- Command references
- Troubleshooting guides
- Engineering documentation best practices

---

# Key Lessons Learned

Throughout this implementation, several important engineering concepts became clearer.

- Artifact repositories separate software packages from source code repositories.
- Blob Stores provide the physical storage layer while repositories organize artifacts logically.
- Cleanup Policies are essential for long-term storage management.
- Linux administration skills are critical for operating self-managed services.
- Cloud infrastructure configuration directly impacts application availability.
- REST APIs enable repeatable automation beyond the graphical user interface.
- Comprehensive documentation improves maintainability and knowledge sharing.

For a detailed discussion of these topics, see:

**`docs/lessons-learned.md`**

---

# Future Improvements

If this environment were expanded into a production-ready deployment, potential improvements would include:

- Enable HTTPS with SSL/TLS certificates
- Deploy behind a reverse proxy
- Integrate external authentication providers (LDAP or SSO)
- Automate infrastructure provisioning using Infrastructure as Code
- Implement automated backup and recovery procedures
- Add monitoring and alerting
- Integrate with CI/CD pipelines
- Implement repository health monitoring
- Configure high availability
- Develop disaster recovery procedures

---

# Documentation Index

This repository contains detailed technical documentation covering every major aspect of the implementation.

| Document | Purpose |
|-----------|---------|
| `docs/project-summary.md` | Executive overview of the project |
| `docs/installation.md` | Installation and configuration guide |
| `docs/repository-management.md` | Repository administration |
| `docs/blob-store-cleanup-policy.md` | Storage and artifact lifecycle management |
| `docs/api-reference.md` | REST API documentation |
| `docs/troubleshooting.md` | Operational troubleshooting |
| `docs/commands.md` | Command reference |
| `docs/lessons-learned.md` | Engineering insights and project reflections |

---

# Repository Assets

This repository includes:

- Architecture diagrams
- AWS implementation
- Technical documentation
- Screenshot gallery
- Command references
- Troubleshooting guide
- Demonstration video
- Lessons learned
- Project summary

---

# References

Official documentation used for additional product reference:

- Nexus Repository Manager Documentation
- Apache Maven Documentation
- Gradle Documentation
- AWS EC2 Documentation
- Ubuntu Server Documentation
- OpenJDK Documentation

> This repository documents a practical implementation completed in an AWS environment and is intended as an educational and portfolio project.

---

# License

This project is licensed under the MIT License.

See the `LICENSE` file for details.

---

# Acknowledgements

This repository represents a hands-on implementation completed to strengthen practical knowledge of artifact repository management, cloud infrastructure, Linux administration, and DevOps engineering practices.

The documentation, diagrams, screenshots, and implementation notes are intended to serve as a reusable technical reference for future deployments and continuous learning.

---

# Author

**Chukwuemeka Peter Eze**

Cloud • DevOps • Platform Engineering

GitHub: https://github.com/Chukwuemeka-Peter-Eze

LinkedIn: https://www.linkedin.com/in/chukwuemekapetereze/

Notion: https://lumpy-bubble-7b0.notion.site/Artifact-Repository-Manager-with-Nexus-3a046a96f974805bbd59ffcf1c64c86e?source=copy_link

---

## Repository Status

**Project Status:** Completed

The deployment was successfully implemented, validated, documented, and organized into a comprehensive engineering portfolio project.

Future enhancements and production-oriented improvements will continue to be explored as part of an ongoing DevOps learning journey.
