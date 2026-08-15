# Nexus Deployment on AWS EC2

## Purpose

This document records the deployment of Nexus Repository Manager on an Ubuntu Linux server hosted on AWS EC2.

The deployment focuses on the operational path from infrastructure access to a running Nexus service.

---

## Deployment Architecture

```text
AWS EC2
   │
   ▼
Ubuntu Linux
   │
   ├── Java Runtime
   │
   ├── Nexus Application
   │
   └── Nexus Data / Working Directory
          │
          ▼
      Nexus Service
          │
          ▼
       Port 8081
          │
          ▼
      Web Interface
```

---

## Infrastructure Boundary

The EC2 instance provides the compute environment for the Nexus service.

Network access is controlled through the EC2 Security Group.

The implementation required:

| Access | Port | Purpose               |
| ------ | ---: | --------------------- |
| SSH    |   22 | Remote administration |
| Nexus  | 8081 | Nexus web interface   |

The Nexus deployment material specifically identifies opening port 8081 as part of making the service accessible through a browser.

---

## Linux Service Identity

A dedicated `nexus` Linux user was created for the application.

The application installation and working directories were assigned to the `nexus` user so that the service did not need to run as root.

Conceptually:

```text
root
 │
 ├── Infrastructure administration
 │
 └── nexus
       │
       ├── Nexus application
       └── Nexus working data
```

This creates a clearer privilege boundary between system administration and application execution.

The practical checklist explicitly included creating the Linux user, changing ownership of the Nexus executable and working directory, configuring Nexus to run as that user, and starting Nexus with the `nexus` account.

---

## Runtime Configuration

Nexus requires a Java runtime.

The deployment therefore followed this sequence:

```text
Ubuntu
  ↓
Java Runtime
  ↓
Nexus Installation
  ↓
Nexus Configuration
  ↓
Service Startup
```

Runtime validation was performed before proceeding with Nexus configuration.

---

## Nexus Installation

The application was installed under the server's application directory.

The installation process consisted of:

1. Preparing the Linux environment.
2. Installing the Java runtime.
3. Downloading the Nexus distribution.
4. Extracting the application.
5. Creating the dedicated `nexus` user.
6. Assigning application and working-directory ownership.
7. Configuring Nexus to run under the dedicated user.
8. Starting Nexus.
9. Validating the running process.
10. Verifying network access to port 8081.

These steps correspond to the deployment sequence documented in the practical material.

---

## Service Validation

A deployment is not considered complete merely because the installation command succeeds.

The running service was validated through:

```text
Process validation
       ↓
Network / port validation
       ↓
Browser access
       ↓
Nexus UI
```

The practical checklist includes process inspection and network-port validation as part of the deployment exercise.

---

## Operational Model

The final runtime model is:

```text
EC2 Instance
    │
    ▼
Ubuntu Linux
    │
    ▼
nexus user
    │
    ▼
Nexus Repository Manager
    │
    ├── Repository configuration
    ├── Artifact management
    ├── REST API
    └── Storage management
```

---

## Deployment Evidence

The repository's screenshots provide evidence for the major deployment stages:

```text
screenshots/
├── 01-ec2-instance.png
├── 02-security-group.png
├── 03-ssh-access.png
├── 04-java-runtime.png
├── 05-nexus-installation.png
└── 06-nexus-service.png
```

These are arranged in the same order as the deployment process so that a reviewer can follow the environment from infrastructure creation to a functioning Nexus service.

---

## Security Considerations

The implementation establishes two important operational boundaries:

### Service Privilege

Nexus runs under a dedicated application user rather than root.

### Network Exposure

The Nexus interface is exposed through a specifically configured port rather than making the entire host unrestricted.

For a production deployment, the Nexus interface would normally be placed behind stronger network controls and encrypted access. Those production controls are outside the scope of this implementation.

---

## Deployment Outcome

The deployment resulted in a functioning Nexus Repository Manager environment running on AWS EC2 and accessible through the Nexus web interface.

The environment then served as the platform for the repository-management, artifact-publishing, API, storage, and cleanup exercises documented in `docs/operations.md`.
