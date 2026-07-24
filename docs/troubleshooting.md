# Nexus Repository Manager Troubleshooting Guide

## Overview

This document contains common issues, troubleshooting approaches, and solutions encountered when deploying and managing Nexus Repository Manager on an AWS EC2 instance.

The purpose of this guide is to provide practical troubleshooting procedures for maintaining a stable Nexus Repository environment.

The troubleshooting areas covered include:

- Nexus startup failures
- Network connectivity issues
- Permission problems
- Java configuration issues
- Artifact publishing failures
- Repository access issues
- Storage-related problems
- REST API troubleshooting

---

# Troubleshooting Approach

When troubleshooting Nexus Repository Manager, the recommended approach is:

```text
Identify Problem

↓

Collect Information

↓

Check Logs

↓

Validate Configuration

↓

Apply Fix

↓

Verify Resolution
```

---

# 1. Nexus Web Interface Is Not Accessible

## Problem

The Nexus dashboard cannot be accessed through the browser.

Example:

```text
http://<EC2-PUBLIC-IP>:8081
```

---

## Possible Causes

Common causes include:

- Nexus service is not running
- Port 8081 is blocked
- Incorrect EC2 Security Group configuration
- Application startup failure
- Network connectivity issue

---

## Troubleshooting Steps

### Check Nexus Process

Verify that Nexus is running.

```bash
ps aux | grep nexus
```

---

### Check Listening Ports

Verify that Nexus is listening on port 8081.

```bash
netstat -lnpt
```

---

### Verify AWS Security Group

Confirm that inbound traffic allows:

```text
Port: 8081

Protocol: TCP
```

---

> Insert Screenshot Here

```text
screenshots/troubleshooting-port.png
```

---

## Resolution

- Start Nexus if the service is stopped.
- Correct Security Group rules.
- Verify the correct public IP address.
- Confirm that the application completed startup.

---

# 2. Nexus Service Fails to Start

## Problem

Nexus does not start successfully.

---

## Possible Causes

- Incorrect file permissions
- Java configuration issues
- Insufficient resources
- Incorrect runtime configuration

---

## Troubleshooting Steps

Check Nexus logs.

Navigate to:

```bash
sonatype-work/nexus3/log/
```

Review:

```text
nexus.log
```

---

Check file ownership:

```bash
ls -la
```

---

Verify Nexus user ownership:

```bash
chown -R nexus:nexus nexus-directory
```

---

> Insert Screenshot Here

```text
screenshots/troubleshooting-startup.png
```

---

## Resolution

Correct:

- Permissions
- Runtime configuration
- Java installation
- User ownership

Restart Nexus after applying changes.

---

# 3. Java Configuration Problems

## Problem

Nexus fails because Java is missing or incorrectly configured.

---

## Symptoms

Possible errors:

- Application does not start
- Java command unavailable
- Unsupported Java version

---

## Troubleshooting Steps

Check Java installation:

```bash
java -version
```

---

Verify Java location:

```bash
which java
```

---

## Resolution

Install and configure the required Java runtime.

Validate:

```bash
java -version
```

---

# 4. Permission Denied Errors

## Problem

Nexus cannot access required files or directories.

---

## Possible Causes

- Incorrect ownership
- Running Nexus with the wrong user
- Restricted file permissions

---

## Troubleshooting Steps

Check directory ownership:

```bash
ls -l
```

---

Verify Nexus user:

```bash
whoami
```

---

Correct ownership:

```bash
chown -R nexus:nexus /opt/nexus
```

---

## Resolution

Ensure:

- Nexus files belong to the Nexus user.
- Nexus is not executed as root.
- Required directories have appropriate permissions.

---

# 5. Artifact Upload Failure

## Problem

Maven or Gradle artifacts fail to upload into Nexus.

---

## Possible Causes

- Incorrect repository URL
- Authentication failure
- Missing permissions
- Incorrect build configuration

---

## Troubleshooting Steps

Verify:

- Repository URL
- Username and password
- Repository existence
- User permissions

---

Check repository configuration.

---

> Insert Screenshot Here

```text
screenshots/troubleshooting-upload.png
```

---

## Resolution

Correct:

- Credentials
- Repository configuration
- User permissions
- Build tool configuration

---

# 6. Repository Cannot Be Found

## Problem

A build tool cannot locate a Nexus repository.

---

## Possible Causes

- Incorrect repository name
- Incorrect URL
- Repository unavailable

---

## Troubleshooting Steps

Verify repositories from Nexus UI.

Check:

```text
Administration

↓

Repositories
```

---

Validate repository endpoint.

---

# 7. REST API Request Failure

## Problem

API requests return errors.

---

## Possible Causes

- Incorrect endpoint
- Authentication problems
- Missing permissions
- Invalid request format

---

## Troubleshooting Steps

Verify:

- API URL
- Authentication credentials
- User permissions
- Request format

---

Example:

```bash
curl -u username:password \
http://server:8081/service/rest/v1/repositories
```

---

> Insert Screenshot Here

```text
screenshots/troubleshooting-api.png
```

---

# 8. Storage Issues

## Problem

Nexus storage usage continues increasing.

---

## Possible Causes

- Too many artifacts
- Missing Cleanup Policies
- Large binary files
- Insufficient storage capacity

---

## Troubleshooting Steps

Check disk usage:

```bash
df -h
```

---

Review Blob Store usage from Nexus:

```text
Administration

↓

Blob Stores
```

---

## Resolution

Possible actions:

- Create Cleanup Policies
- Remove unnecessary artifacts
- Increase storage capacity
- Review artifact retention strategy

---

# 9. Cleanup Task Does Not Remove Artifacts

## Problem

Cleanup Policy execution completes but artifacts remain.

---

## Possible Causes

- Policy rules do not match artifacts
- Repository is not assigned
- Task did not execute correctly

---

## Troubleshooting Steps

Verify:

- Cleanup Policy configuration
- Repository assignment
- Task execution status

---

> Insert Screenshot Here

```text
screenshots/troubleshooting-cleanup.png
```

---

# 10. Useful Diagnostic Commands

## Check Nexus Process

```bash
ps aux | grep nexus
```

---

## Check Port Usage

```bash
netstat -lnpt
```

---

## Check Disk Space

```bash
df -h
```

---

## Check Running User

```bash
whoami
```

---

## Review Logs

```bash
tail -f nexus.log
```

---

# Operational Best Practices

To reduce future issues:

- Monitor Nexus logs regularly.
- Maintain sufficient storage capacity.
- Apply cleanup policies.
- Backup repository data.
- Keep operating system packages updated.
- Restrict administrative permissions.
- Document configuration changes.
- Monitor EC2 resource utilization.

---

# Troubleshooting Checklist

Successful troubleshooting should confirm:

- Nexus process is running
- Port 8081 is reachable
- Java environment is healthy
- Permissions are correct
- Repositories are accessible
- Artifact uploads succeed
- REST API responds correctly
- Storage is managed properly
- Cleanup policies execute successfully

---

# Conclusion

Troubleshooting Nexus Repository Manager requires understanding the interaction between cloud infrastructure, Linux administration, application configuration, storage management, and repository operations.

This troubleshooting guide provides a structured approach for identifying, diagnosing, and resolving common operational issues while maintaining a reliable artifact management platform.
