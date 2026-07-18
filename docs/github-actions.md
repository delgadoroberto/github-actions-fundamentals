# GitHub Actions Fundamentals

GitHub Actions is GitHub's native Continuous Integration and Continuous Delivery (CI/CD) platform. It allows developers to automate software development workflows directly from a GitHub repository.

With GitHub Actions, you can automatically build, test, analyze, package, and deploy applications whenever specific events occur.

---

# Why GitHub Actions?

Automation reduces repetitive work and improves software quality.

Common use cases include:

- Running automated tests
- Static Application Security Testing (SAST)
- Dependency scanning
- Building Docker images
- Continuous Integration
- Continuous Deployment
- Infrastructure as Code validation
- Automated documentation generation

---

# Core Components

GitHub Actions is composed of several building blocks.

## Workflow

A workflow is an automated process defined in a YAML file located under:

```text
.github/workflows/
```

A repository may contain multiple workflows.

Example:

```yaml
name: Basic Pipeline
```

---

## Events

An event determines when a workflow starts.

Examples include:

```yaml
on:
  push:
```

Other common events are:

- pull_request
- workflow_dispatch
- schedule
- release
- issues

---

## Jobs

A workflow contains one or more jobs.

Jobs run independently unless dependencies are defined.

Example:

```yaml
jobs:
  fundamentals:
```

---

## Runner

A runner is the virtual machine that executes a workflow.

GitHub provides hosted runners such as:

- ubuntu-latest
- windows-latest
- macos-latest

Example:

```yaml
runs-on: ubuntu-latest
```

---

## Steps

Each job consists of multiple steps.

A step performs a single task.

Examples:

- Checkout repository
- Install dependencies
- Execute tests
- Build software
- Upload artifacts

---

## Actions

Actions are reusable components that perform common tasks.

Example:

```yaml
uses: actions/checkout@v4
```

This Action clones the repository into the runner.

---

## Shell Commands

A step may execute shell commands directly.

Example:

```yaml
run: |
  pwd
  ls -lah
```

---

## Variables

GitHub automatically exposes contextual variables.

Examples:

```text
github.actor
github.repository
github.workflow
github.ref_name
github.sha
```

These variables allow workflows to access information about the current execution.

---

## Artifacts

Artifacts allow workflows to preserve files after execution.

Typical examples include:

- Reports
- Test results
- Logs
- Build outputs
- Security scan reports

Example:

```yaml
uses: actions/upload-artifact@v4
```

Artifacts can be downloaded directly from the Actions interface.

---

# Workflow Lifecycle

A typical workflow execution follows these stages:

```text
Developer Push
        │
        ▼
GitHub Event
        │
        ▼
Workflow Starts
        │
        ▼
Runner Provisioned
        │
        ▼
Repository Checkout
        │
        ▼
Execute Steps
        │
        ▼
Generate Artifacts
        │
        ▼
Workflow Completed
```

---

# Best Practices

When creating GitHub Actions workflows:

- Keep workflows simple and modular.
- Use descriptive job and step names.
- Store secrets using GitHub Secrets.
- Avoid hardcoded credentials.
- Keep workflow files well documented.
- Reuse Actions whenever possible.
- Upload useful artifacts.
- Review execution logs regularly.

---

# Next Steps

Once you understand these fundamentals, you are ready to explore more advanced topics such as:

- Matrix builds
- Dependency caching
- Reusable workflows
- Docker automation
- Security scanning
- CI/CD pipelines
- DevSecOps automation

These topics are covered in more advanced repositories within this GitHub portfolio.
