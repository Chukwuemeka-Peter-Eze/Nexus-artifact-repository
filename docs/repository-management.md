# Repository Management Guide

## Overview

This document explains how repositories were created, organized, and managed within the Nexus Repository Manager deployed on AWS.

A repository in Nexus is a logical location used to store, organize, proxy, or aggregate software artifacts. Proper repository management is essential for maintaining an efficient software delivery pipeline and ensuring reliable artifact distribution.

This guide documents the repository management activities completed during this project.

---

# Objectives

The repository management implementation focused on the following objectives:

- Create and configure hosted repositories
- Understand proxy repositories
- Understand group repositories
- Configure repository storage
- Assign Blob Stores
- Configure repository policies
- Verify repository accessibility
- Organize artifacts using repository best practices

---

# Repository Architecture

```text
                     Nexus Repository Manager

            ┌──────────────┼──────────────┐
            │              │              │

            ▼              ▼              ▼

      Hosted Repo     Proxy Repo     Group Repo

            │              │              │
            └──────────────┼──────────────┘

                           ▼

                      Blob Store

                           ▼

                  Physical Storage
```

---

# Repository Types

Nexus Repository Manager supports multiple repository types, each designed for a specific purpose within the software delivery lifecycle.

During this project, the repository types were explored to understand how they support artifact management.

---

# Hosted Repository

## Purpose

Hosted repositories store internally produced artifacts that originate from development teams within an organization.

Typical examples include:

- Internal Java libraries
- Release artifacts
- Snapshot artifacts
- Application packages
- Organization-specific dependencies

Hosted repositories serve as the central storage location for artifacts generated during software builds.

---

## Characteristics

- Supports artifact uploads
- Stores internally generated packages
- Version controlled
- Fully managed by administrators
- Supports release and snapshot repositories

---

> **Insert Screenshot Here**

```text
screenshots/13-hosted-repository.png
```

---

# Hosted Repository Configuration

The hosted repository was configured by defining:

- Repository name
- Repository format
- Version policy
- Deployment policy
- Blob Store assignment
- Storage configuration

After creation, the repository became available for Maven and Gradle artifact publishing.

---

> **Insert Screenshot Here**

```text
screenshots/14-hosted-settings.png
```

---

# Proxy Repository

## Purpose

Proxy repositories act as intermediaries between development teams and external package repositories.

Instead of downloading dependencies directly from the internet every time, Nexus caches packages locally after the first request.

This improves download performance and reduces external network dependency.

---

## Benefits

- Faster dependency retrieval
- Reduced internet bandwidth usage
- Improved build reliability
- Local package caching
- Centralized dependency management

---

> **Insert Screenshot Here**

```text
screenshots/15-proxy-repository.png
```

---

# Proxy Repository Workflow

```text
Developer

↓

Build Tool

↓

Proxy Repository

↓

External Repository

↓

Package Download

↓

Cached in Nexus

↓

Future Requests Served Locally
```

---

# Group Repository

## Purpose

Group repositories combine multiple repositories behind a single endpoint.

Rather than configuring separate repository URLs, developers interact with one consolidated repository.

---

## Advantages

- Simplified build configuration
- Single repository endpoint
- Improved dependency resolution
- Easier administration
- Centralized package access

---

> **Insert Screenshot Here**

```text
screenshots/16-group-repository.png
```

---

# Repository Storage

Each repository is associated with a Blob Store where artifacts are physically stored.

The repository provides the logical organization while the Blob Store manages the underlying storage.

```text
Repository

↓

Blob Store

↓

Physical Disk Storage
```

---

> **Insert Screenshot Here**

```text
screenshots/17-storage-configuration.png
```

---

# Repository Policies

Several repository policies influence how artifacts are managed.

Examples include:

- Version policy
- Deployment policy
- Cleanup policy
- Storage policy
- Write permissions

These settings determine how artifacts are uploaded, retained, and maintained over time.

---

> **Insert Screenshot Here**

```text
screenshots/18-repository-policies.png
```

---

# Repository Access

Repository access was validated after configuration to confirm that authorized users could browse repositories and publish artifacts successfully.

Validation activities included:

- Opening repository views
- Browsing repository contents
- Confirming repository availability
- Verifying upload permissions
- Reviewing repository metadata

---

> **Insert Screenshot Here**

```text
screenshots/19-repository-validation.png
```

---

# Repository Management Best Practices

The following practices were applied or considered during this implementation:

- Use meaningful repository names.
- Separate release and snapshot artifacts where appropriate.
- Assign repositories to the correct Blob Store.
- Restrict upload permissions to authorized users.
- Regularly review repository contents.
- Apply Cleanup Policies to manage storage growth.
- Monitor repository health and available storage.
- Document repository configurations for future maintenance.

---

# Validation Checklist

Repository configuration was considered successful after verifying the following:

- Hosted repository created
- Proxy repository reviewed
- Group repository reviewed
- Repository settings configured
- Blob Store assigned
- Repository accessible
- Repository browsing successful
- Upload permissions verified
- Repository structure documented

---

# Lessons Learned

Managing repositories effectively is a foundational skill in DevOps and software delivery.

Through this implementation, the following concepts became clear:

- Different repository types solve different operational challenges.
- Hosted repositories provide centralized storage for internal software artifacts.
- Proxy repositories improve dependency management through caching.
- Group repositories simplify client configuration by presenting multiple repositories as a single endpoint.
- Logical repository organization combined with proper storage management supports scalable artifact lifecycle management.

---

# Outcome

At the completion of this implementation, the Nexus Repository Manager was configured with the necessary repository structures to support artifact storage, retrieval, and lifecycle management in an AWS-hosted environment.

This repository configuration provides a solid foundation for publishing artifacts, integrating with build tools, and supporting future CI/CD workflows.
