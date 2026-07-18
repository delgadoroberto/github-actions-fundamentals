# Workflow Architecture

## Overview

This document describes the architecture of the GitHub Actions workflow implemented in this laboratory.

The workflow demonstrates the fundamental components of a Continuous Integration (CI) pipeline using GitHub-hosted runners and native GitHub Actions.

Although intentionally simple, the architecture reflects the same execution model used by production-grade CI/CD pipelines.

---

# High-Level Architecture

```text
                +----------------------+
                |      Developer       |
                +----------+-----------+
                           |
                     git push / Manual Run
                           |
                           ▼
                +----------------------+
                |   GitHub Repository  |
                +----------+-----------+
                           |
                           ▼
                +----------------------+
                | GitHub Actions Event |
                +----------+-----------+
                           |
                           ▼
                +----------------------+
                |     Workflow YAML    |
                | basic-pipeline.yml   |
                +----------+-----------+
                           |
                           ▼
                +----------------------+
                | GitHub Hosted Runner |
                |   ubuntu-latest      |
                +----------+-----------+
                           |
        +------------------+------------------+
        |                  |                  |
        ▼                  ▼                  ▼
 Repository         System Information     Development Tools
 Checkout              Collection             Validation
        |                  |                  |
        +------------------+------------------+
                           |
                           ▼
                +----------------------+
                | Generate Artifact    |
                +----------+-----------+
                           |
                           ▼
                +----------------------+
                | Upload Artifact      |
                +----------+-----------+
                           |
                           ▼
                +----------------------+
                | Workflow Completed   |
                +----------------------+
```

---

# Execution Flow

Each workflow execution follows the same lifecycle.

1. A workflow event is triggered.
2. GitHub provisions a temporary runner.
3. The repository is cloned.
4. Workflow steps execute sequentially.
5. An artifact is generated.
6. The artifact is uploaded.
7. The runner is destroyed.

Since GitHub-hosted runners are ephemeral, every execution starts from a clean environment.

---

# Components

## Repository

Contains:

- Workflow definitions
- Documentation
- Scripts
- Project files

Repository path:

```text
.github/workflows/
```

---

## Workflow

The workflow defines:

- Trigger events
- Jobs
- Execution environment
- Steps
- Artifact generation

---

## Runner

Execution environment:

```text
ubuntu-latest
```

The runner provides pre-installed tools such as:

- Git
- Python
- Bash
- Docker
- Node.js

The virtual machine exists only during workflow execution.

---

## Actions

The workflow currently uses two official GitHub Actions.

| Action | Purpose |
|---------|---------|
| actions/checkout | Clone repository |
| actions/upload-artifact | Publish generated files |

Official Actions are maintained by GitHub and represent best practice for common tasks.

---

## Shell Commands

Most workflow logic is implemented using Bash commands.

Examples include:

- date
- whoami
- hostname
- ls
- mkdir
- echo

This keeps the workflow simple while introducing core automation concepts.

---

# Artifact Architecture

The workflow generates:

```text
output/
└── lab-info.txt
```

This file contains execution metadata such as:

- Workflow name
- Repository
- Actor
- Execution date
- Branch
- Commit

The artifact is uploaded and stored by GitHub after successful execution.

---

# Security Considerations

This educational workflow intentionally avoids:

- Hardcoded credentials
- Personal Access Tokens
- Secrets in source code
- Third-party Actions without version pinning

When building production workflows, additional controls should include:

- GitHub Secrets
- Least privilege permissions
- Branch protection
- Required reviews
- Dependency scanning
- Code scanning
- Signed commits

---

# Design Principles

The workflow was designed following these principles:

- Simplicity
- Readability
- Reproducibility
- Incremental learning
- Clear separation of responsibilities

Each step demonstrates a single concept to simplify understanding.

---

# Future Architecture Evolution

As the laboratory evolves, additional capabilities may be incorporated.

Possible future additions include:

- Matrix builds
- Dependency caching
- Multiple jobs
- Job dependencies
- Conditional execution
- Reusable workflows
- Docker image builds
- Security scanning
- Automated testing
- Release automation

These improvements build upon the architecture introduced in this repository.

---

# Conclusion

This architecture provides a practical introduction to GitHub Actions by illustrating the complete lifecycle of a workflow, from event trigger to artifact publication.

The concepts learned here establish the foundation for more advanced CI/CD and DevSecOps pipelines.
