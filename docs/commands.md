# Command Reference Guide

## Overview

This document provides a centralized reference for the Linux, AWS, Java, Nexus Repository Manager, Maven, Gradle, and REST API commands used throughout this project.

The commands are organized by implementation phase, making it easier to revisit installation steps, administrative tasks, troubleshooting procedures, and artifact management workflows.

---

# Table of Contents

1. AWS Commands
2. Linux Commands
3. Java Commands
4. Nexus Installation Commands
5. Nexus Administration
6. Repository Management
7. Maven Commands
8. Gradle Commands
9. REST API Examples
10. Process Monitoring
11. File Management
12. Networking
13. Troubleshooting Commands
14. Useful Linux Shortcuts

---

# AWS Commands

## Connect to EC2

```bash
ssh -i your-key.pem ubuntu@<EC2-PUBLIC-IP>
```

Purpose:

Connect securely to the AWS EC2 instance hosting Nexus Repository Manager.

---

## Verify Current User

```bash
whoami
```

---

## Verify Server Information

```bash
hostname
```

```bash
hostnamectl
```

---

## Check Operating System

```bash
cat /etc/os-release
```

---

# Linux Commands

## Update Package Repository

```bash
sudo apt update
```

---

## Upgrade Installed Packages

```bash
sudo apt upgrade
```

---

## Install Required Packages

```bash
sudo apt install wget
```

```bash
sudo apt install unzip
```

```bash
sudo apt install curl
```

---

## List Files

```bash
ls
```

```bash
ls -la
```

---

## Change Directory

```bash
cd
```

```bash
cd /opt
```

---

## Display Current Directory

```bash
pwd
```

---

# Java Commands

## Verify Java Installation

```bash
java -version
```

---

## Verify Java Compiler

```bash
javac -version
```

---

# Nexus Installation Commands

## Download Nexus

```bash
wget <Nexus-Download-URL>
```

---

## Extract Archive

```bash
tar -xvzf nexus.tar.gz
```

---

## Rename Directory (Optional)

```bash
mv nexus-* nexus
```

---

## Create Nexus User

```bash
sudo adduser nexus
```

---

## Change Ownership

```bash
sudo chown -R nexus:nexus /opt/nexus
```

```bash
sudo chown -R nexus:nexus /opt/sonatype-work
```

---

## Switch User

```bash
sudo su - nexus
```

---

## Start Nexus

```bash
/opt/nexus/bin/nexus start
```

---

## Stop Nexus

```bash
/opt/nexus/bin/nexus stop
```

---

## Restart Nexus

```bash
/opt/nexus/bin/nexus restart
```

---

## Check Nexus Status

```bash
/opt/nexus/bin/nexus status
```

---

# Repository Management

Typical administrative tasks completed during this project included:

- Creating hosted repositories
- Reviewing proxy repositories
- Reviewing group repositories
- Assigning Blob Stores
- Configuring Cleanup Policies
- Managing repository permissions
- Validating repository availability

> **Insert Screenshot Here**

```text
screenshots/39-repository-administration.png
```

---

# Maven Commands

## Clean Project

```bash
mvn clean
```

---

## Compile Project

```bash
mvn compile
```

---

## Run Tests

```bash
mvn test
```

---

## Package Project

```bash
mvn package
```

---

## Install Artifact Locally

```bash
mvn install
```

---

## Publish Artifact

```bash
mvn deploy
```

---

> **Insert Screenshot Here**

```text
screenshots/40-maven-deploy.png
```

---

# Gradle Commands

## Clean Project

```bash
gradle clean
```

---

## Build Project

```bash
gradle build
```

---

## Run Tests

```bash
gradle test
```

---

## Publish Artifact

```bash
gradle publish
```

---

## View Available Tasks

```bash
gradle tasks
```

---

> **Insert Screenshot Here**

```text
screenshots/41-gradle-publish.png
```

---

# REST API Examples

The project included exploring the Nexus REST API to retrieve repository information, components, and assets.

Examples of API interactions performed:

- List repositories
- Query repository components
- Query repository assets

> **Insert Screenshot Here**

```text
screenshots/42-api-requests.png
```

> Replace the placeholders below with the API requests you actually executed during the project.

```text
GET /repositories

GET /components

GET /assets
```

---

# Process Monitoring

## View Running Processes

```bash
ps -ef
```

---

## Search for Nexus Process

```bash
ps -ef | grep nexus
```

---

## View System Resource Usage

```bash
top
```

---

## Interactive Process Viewer

```bash
htop
```

---

# File Management

## Copy Files

```bash
cp source destination
```

---

## Move Files

```bash
mv source destination
```

---

## Remove Files

```bash
rm filename
```

---

## Remove Directory

```bash
rm -rf directory
```

---

## Create Directory

```bash
mkdir directory-name
```

---

# Networking Commands

## Display Listening Ports

```bash
ss -tuln
```

---

## Test Connectivity

```bash
ping <host>
```

---

## Retrieve HTTP Headers

```bash
curl -I http://<server>
```

---

# Log Management

## View Nexus Logs

```bash
tail -f /opt/sonatype-work/nexus3/log/nexus.log
```

---

## View System Logs

```bash
journalctl
```

---

# Troubleshooting Commands

## Check Disk Usage

```bash
df -h
```

---

## Check Memory Usage

```bash
free -h
```

---

## Check CPU Information

```bash
lscpu
```

---

## Check Running Services

```bash
systemctl status
```

---

## Verify Network Configuration

```bash
ip addr
```

---

# Useful Linux Shortcuts

| Command | Purpose |
|---------|---------|
| `history` | Display command history |
| `clear` | Clear terminal |
| `exit` | Close shell session |
| `pwd` | Show current directory |
| `whoami` | Display current user |
| `man <command>` | View command manual |
| `which <command>` | Locate executable |
| `echo` | Print text or variables |

---

# Quick Validation Checklist

Use the following checklist after completing your implementation:

- Connected to AWS EC2 successfully
- Verified Java installation
- Downloaded and configured Nexus
- Started Nexus service
- Accessed the web interface
- Reviewed repository configuration
- Published Maven artifact
- Published Gradle artifact
- Explored REST API endpoints
- Configured Blob Store
- Created Cleanup Policy
- Executed Cleanup Task
- Verified artifact storage
- Documented implementation with screenshots

---

# Notes

This guide is intended to serve as a quick-reference companion to the project's detailed documentation. As you expand your environment or automate additional workflows, you can add new commands, administrative procedures, and API examples to keep this reference current.

> **Tip:** Where this document contains placeholders (such as the Nexus download URL or REST API requests), replace them with the exact commands and endpoints you used during your implementation so the repository accurately reflects your work.
