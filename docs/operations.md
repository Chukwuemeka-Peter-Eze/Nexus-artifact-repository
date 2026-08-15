# Nexus Repository Operations

## Purpose

This document records the operational work performed after Nexus Repository Manager was deployed.

The focus is on the artifact-management lifecycle:

```text
Repository
   ↓
Artifact Publishing
   ↓
Component / Asset
   ↓
API Access
   ↓
Storage
   ↓
Cleanup
```

---

## Repository Types

Nexus supports different repository behaviors.

### Hosted Repository

A hosted repository is used for artifacts produced internally.

```text
Build
  ↓
Artifact
  ↓
Hosted Repository
```

This is the repository type used when a build system publishes an internally produced artifact to Nexus.

### Proxy Repository

A proxy repository acts as an intermediary to another repository.

```text
Build / Consumer
       ↓
     Nexus
       ↓
External Repository
```

This provides a controlled access point to external artifact sources.

### Group Repository

A group repository provides an aggregated access point across multiple repositories.

```text
             Group Repository
                    │
          ┌─────────┴─────────┐
          ▼                   ▼
       Hosted               Proxy
     Repository           Repository
```

The implementation covered the three repository types and their different responsibilities.

---

## Artifact Publishing

Java artifacts were built and published using both Maven and Gradle.

The publishing flow is:

```text
Java Source
    ↓
Build Tool
    ↓
JAR Artifact
    ↓
Nexus Hosted Repository
```

The build tool must know:

* Nexus repository address
* Repository credentials
* Artifact coordinates
* Publishing configuration

The practical implementation included creating a Nexus user with permission to upload artifacts and publishing Java JAR files through Maven and Gradle.

---

## Maven Publishing

Maven acts as the build and publishing client.

```text
Maven Project
     │
     ▼
mvn build
     │
     ▼
JAR Artifact
     │
     ▼
Nexus Maven Repository
```

The resulting artifact can then be inspected from Nexus after publication.

Evidence:

```text
screenshots/10-maven-artifact.png
screenshots/12-published-artifact.png
```

---

## Gradle Publishing

Gradle follows the same general artifact lifecycle:

```text
Gradle Project
     │
     ▼
Gradle Build
     │
     ▼
JAR Artifact
     │
     ▼
Nexus Repository
```

Evidence:

```text
screenshots/11-gradle-artifact.png
screenshots/12-published-artifact.png
```

---

## Components and Assets

Nexus distinguishes between a logical component and the physical assets associated with it.

```text
Component
   │
   ├── Asset
   ├── Asset
   └── Asset
```

A component represents the artifact conceptually, while assets represent the actual files stored by Nexus.

This distinction becomes important when working with the REST API because repository queries can return components and assets separately.

---

## REST API

The Nexus REST API provides programmatic access to repository information and artifact data.

The implementation queried:

* Repositories
* Components
* Assets

The conceptual request path is:

```text
HTTP Client
     │
     │ GET / API Request
     ▼
Nexus REST API
     │
     ├── Repositories
     ├── Components
     └── Assets
```

Command-line HTTP clients such as `curl` can be used to interact with the API.

The practical exercise required authentication with a Nexus user and included querying repositories, components, and assets.

Evidence:

```text
screenshots/13-nexus-api.png
screenshots/14-repository-query.png
screenshots/15-component-asset-query.png
```

---

## Blob Stores

A Blob Store provides the storage layer used by Nexus for repository content.

The logical relationship is:

```text
Repository
    ↓
Component
    ↓
Asset
    ↓
Blob Store
    ↓
Physical Storage
```

A new Blob Store was created as part of the implementation.

Evidence:

```text
screenshots/16-blob-store.png
```

---

## Cleanup Policies

Artifact repositories require lifecycle management because retained artifacts consume storage.

Nexus Cleanup Policies allow conditions to be defined for identifying artifacts that should be removed.

The implementation covered:

```text
Create Cleanup Policy
        ↓
Attach Policy to Repository
        ↓
Execute Cleanup Task
        ↓
Validate Result
```

The underlying concept is to define retention conditions and apply them through Nexus tasks.

Evidence:

```text
screenshots/17-cleanup-policy.png
screenshots/18-cleanup-task.png
```

---

## Operational Relationships

The major Nexus concepts explored in this project are connected:

```text
                 Build System
                /            \
             Maven          Gradle
                \            /
                 \          /
                  ▼        ▼
                Artifact
                    │
                    ▼
              Nexus Repository
                    │
                    ▼
                Component
                    │
                    ▼
                  Assets
                    │
                    ▼
                Blob Store
                    │
                    ▼
             Physical Storage
                    │
                    ▼
             Cleanup Policy
```

The REST API provides an additional programmatic interface across this model.

```text
                   REST API
                      │
        ┌─────────────┼─────────────┐
        ▼             ▼             ▼
   Repository     Component       Asset
```

---

## Operational Validation

The operational work was validated by observing the results of each major activity rather than treating configuration as the final outcome.

Validation included:

* Repository creation
* Artifact publication
* Artifact visibility in Nexus
* Repository API queries
* Component queries
* Asset queries
* Blob Store creation
* Cleanup Policy creation
* Repository association
* Manual cleanup task execution

These activities correspond directly to the practical checklist for repository management, artifact publishing, API interaction, Blob Stores, and Cleanup Policies.

---

## Operational Model

The resulting system can be understood as an artifact platform rather than simply a web application:

```text
                  Developer
                      │
                      ▼
                 Build System
                      │
                ┌─────┴─────┐
                ▼           ▼
             Maven       Gradle
                │           │
                └─────┬─────┘
                      ▼
                 Nexus Hosted
                  Repository
                      │
             ┌────────┴────────┐
             ▼                 ▼
         Component           Assets
             │                 │
             └────────┬────────┘
                      ▼
                  Blob Store
                      │
                      ▼
                 Stored Data
                      │
                      ▼
                Cleanup Policy
```

This model connects artifact production, storage, retrieval, API access, and lifecycle management into one operational system.
