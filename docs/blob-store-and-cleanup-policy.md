# Blob Store and Cleanup Policy Guide

## Overview

This document explains the implementation of Blob Stores and Cleanup Policies within the Nexus Repository Manager deployed on AWS.

Blob Stores provide the physical storage layer for software artifacts, while Cleanup Policies automate the removal of obsolete artifacts to optimize storage utilization and simplify repository maintenance.

Both features are essential for managing artifact lifecycle, storage efficiency, and long-term repository health.

---

# Objectives

The implementation focused on the following objectives:

- Understand Blob Store architecture
- Create and configure a Blob Store
- Associate repositories with a Blob Store
- Understand artifact storage
- Create Cleanup Policies
- Attach Cleanup Policies to repositories
- Execute Cleanup Tasks
- Validate artifact lifecycle management

---

# Storage Architecture

```text
Developer

↓

Build Tool

↓

Artifact

↓

Hosted Repository

↓

Blob Store

↓

Physical Storage
```

The repository organizes artifacts logically, while the Blob Store manages where the files are physically stored.

---

# What is a Blob Store?

A Blob Store is the storage backend used by Nexus Repository Manager to hold uploaded artifacts.

Instead of storing files directly inside repositories, repositories reference a Blob Store that manages the physical storage.

This separation provides flexibility, scalability, and easier storage management.

---

# Blob Store Responsibilities

A Blob Store is responsible for:

- Storing uploaded artifacts
- Managing binary files
- Supporting repository storage
- Improving storage organization
- Enabling scalable repository management

---

# Blob Store Workflow

```text
Artifact Upload

↓

Repository

↓

Blob Store

↓

Disk Storage
```

When an artifact is uploaded:

1. The repository receives the upload.
2. Metadata is recorded.
3. The binary file is stored inside the configured Blob Store.
4. Future downloads retrieve the artifact from the Blob Store.

---

# Creating a Blob Store

A dedicated Blob Store was created during this project to provide centralized storage for repositories.

Configuration included:

- Blob Store name
- Storage location
- Capacity planning
- Repository assignment

---

> **Insert Screenshot Here**

```text
screenshots/24-create-blob-store.png
```

---

# Assigning Repositories to a Blob Store

Repositories were configured to use the newly created Blob Store.

This ensures all uploaded artifacts are stored in the designated storage backend.

---

> **Insert Screenshot Here**

```text
screenshots/25-blob-store-assignment.png
```

---

# Blob Store Benefits

Using Blob Stores provides several operational advantages:

- Centralized storage management
- Simplified repository administration
- Better scalability
- Improved backup planning
- Efficient disk utilization
- Separation of logical repositories from physical storage

---

# Understanding Cleanup Policies

As artifact repositories grow, outdated or unused artifacts consume storage space and increase maintenance effort.

Cleanup Policies automate the removal of artifacts that meet predefined criteria, helping maintain repository health.

---

# Why Cleanup Policies Matter

Cleanup Policies help organizations:

- Reduce storage consumption
- Remove obsolete artifacts
- Improve repository performance
- Simplify maintenance
- Control repository growth
- Support artifact lifecycle management

---

# Cleanup Policy Workflow

```text
Artifacts

↓

Evaluate Rules

↓

Cleanup Policy

↓

Cleanup Task

↓

Delete Eligible Artifacts

↓

Blob Store Updated
```

---

# Creating a Cleanup Policy

A Cleanup Policy was created to define retention rules for repository artifacts.

Configuration included:

- Policy name
- Retention criteria
- Selection rules

The policy identifies artifacts that are eligible for removal based on the configured rules.

---

> **Insert Screenshot Here**

```text
screenshots/26-create-cleanup-policy.png
```

---

# Attaching a Cleanup Policy

After creating the policy, it was associated with the appropriate repository.

Once attached, the repository became eligible for automated cleanup operations.

---

> **Insert Screenshot Here**

```text
screenshots/27-attach-cleanup-policy.png
```

---

# Executing a Cleanup Task

To validate the configuration, a Cleanup Task was manually executed.

This task evaluated repository contents against the configured Cleanup Policy and processed eligible artifacts.

---

> **Insert Screenshot Here**

```text
screenshots/28-run-cleanup-task.png
```

---

# Verifying Cleanup Results

After execution, repository contents were reviewed to confirm that the cleanup process completed successfully.

Validation included:

- Repository inspection
- Artifact verification
- Storage review
- Task status confirmation

---

> **Insert Screenshot Here**

```text
screenshots/29-cleanup-results.png
```

---

# Storage Lifecycle

The artifact lifecycle can be summarized as follows:

```text
Artifact Created

↓

Artifact Uploaded

↓

Repository

↓

Blob Store

↓

Artifact Consumed

↓

Cleanup Policy Evaluation

↓

Cleanup Task

↓

Artifact Removed (if eligible)
```

---

# Best Practices

The following practices support effective Blob Store and Cleanup Policy management:

## Blob Stores

- Plan storage capacity before deployment.
- Assign repositories to the appropriate Blob Store.
- Monitor available disk space.
- Implement regular backups.
- Document storage configurations.

## Cleanup Policies

- Review retention rules before execution.
- Test policies in non-production environments.
- Schedule cleanup tasks during maintenance windows.
- Periodically review policy effectiveness.
- Monitor cleanup task results.

---

# Validation Checklist

The implementation was considered successful after verifying:

- Blob Store created
- Blob Store configured
- Repository assigned to Blob Store
- Cleanup Policy created
- Cleanup Policy attached
- Cleanup Task executed
- Repository validated after cleanup
- Storage lifecycle documented

---

# Lessons Learned

Implementing Blob Stores and Cleanup Policies reinforced several important concepts:

- Repositories provide logical organization, while Blob Stores manage physical storage.
- Separating storage from repository configuration improves scalability.
- Cleanup Policies automate routine maintenance tasks.
- Regular storage management supports repository performance and operational efficiency.
- Artifact lifecycle management is an important aspect of maintaining a healthy software delivery platform.

---

# Outcome

By successfully configuring a Blob Store and implementing Cleanup Policies, this project demonstrated practical experience with storage management and artifact lifecycle administration in Nexus Repository Manager.

The implementation highlights how automated maintenance and structured storage management contribute to scalable, reliable, and maintainable artifact repository operations.
