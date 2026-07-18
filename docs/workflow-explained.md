# Understanding the Workflow

This document explains the `basic-pipeline.yml` workflow used throughout this laboratory.

The objective is to understand how GitHub Actions executes a workflow from start to finish.

---

# Workflow Overview

The workflow is located at:

```text
.github/workflows/basic-pipeline.yml
```

It is automatically executed whenever changes are pushed to the `main` branch or when it is manually triggered from the GitHub Actions interface.

---

# Workflow Structure

A GitHub Actions workflow is divided into several sections.

```yaml
name:
on:
jobs:
```

Each section has a specific purpose.

---

# Workflow Name

```yaml
name: GitHub Actions Fundamentals
```

The `name` field defines the workflow name displayed in the GitHub Actions interface.

Using descriptive names makes it easier to identify workflows in repositories containing multiple pipelines.

---

# Trigger Events

```yaml
on:
  push:
    branches:
      - main

  workflow_dispatch:
```

The workflow starts when:

- Code is pushed to the `main` branch.
- A user manually starts the workflow from the **Actions** tab.

This combination is commonly used for development and learning environments.

---

# Jobs

```yaml
jobs:
  fundamentals:
```

A workflow contains one or more jobs.

Each job runs on its own runner.

Jobs can execute independently or depend on previous jobs.

This laboratory contains a single job named **fundamentals**.

---

# Runner

```yaml
runs-on: ubuntu-latest
```

GitHub automatically provisions a fresh Ubuntu virtual machine.

The runner includes many development tools pre-installed, including:

- Git
- Python
- Bash
- Docker
- Node.js

Each workflow execution starts with a clean environment.

---

# Checkout Action

```yaml
uses: actions/checkout@v4
```

This Action clones the repository into the runner.

Without this step, the workflow would not have access to the repository files.

It is one of the most commonly used GitHub Actions.

---

# Display Runner Information

```yaml
run: |
```

This step executes several Linux commands.

Examples include:

- `date`
- `whoami`
- `hostname`
- `cat /etc/os-release`

These commands help identify the execution environment.

---

# Display Installed Tools

The workflow displays the versions of common development tools.

Examples include:

- Python
- Git
- Bash

This information is useful for troubleshooting and validating the execution environment.

---

# Repository Contents

```bash
ls -lah
```

This command lists all files inside the repository after checkout.

It confirms that the repository has been cloned successfully.

---

# Creating an Artifact

The workflow creates the file:

```text
output/lab-info.txt
```

The file contains information such as:

- Workflow name
- Repository name
- Execution date
- Branch
- Triggering user

This demonstrates how workflows can generate reports during execution.

---

# Uploading the Artifact

```yaml
uses: actions/upload-artifact@v4
```

Artifacts are stored by GitHub after the workflow finishes.

They can be downloaded from the **Actions** page.

Typical artifacts include:

- Test reports
- Security scan reports
- Build outputs
- Log files
- Documentation

---

# Workflow Summary

The final step prints a summary containing information such as:

- Repository
- Branch
- Commit SHA

This makes it easier to identify which commit produced the workflow execution.

---

# Execution Flow

```text
Push or Manual Execution
            │
            ▼
Workflow Triggered
            │
            ▼
Runner Created
            │
            ▼
Checkout Repository
            │
            ▼
Display System Information
            │
            ▼
Display Installed Tools
            │
            ▼
List Repository Files
            │
            ▼
Generate Artifact
            │
            ▼
Upload Artifact
            │
            ▼
Workflow Completed
```

---

# Key Takeaways

After completing this workflow, you should understand:

- How GitHub Actions workflows are structured.
- How events trigger workflows.
- How jobs execute on runners.
- How steps are processed sequentially.
- How Actions extend workflow functionality.
- How artifacts preserve workflow outputs.
- How to inspect workflow logs and execution history.

These concepts provide the foundation for more advanced CI/CD and DevSecOps pipelines.
