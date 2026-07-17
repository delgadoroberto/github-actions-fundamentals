# GitHub Actions Fundamentals

[![GitHub Actions](https://img.shields.io/badge/GitHub-Actions-2088FF?logo=githubactions&logoColor=white)](https://github.com/features/actions)
[![YAML](https://img.shields.io/badge/YAML-Configuration-red?logo=yaml)](https://yaml.org/)
[![CI](https://img.shields.io/badge/CI-Continuous%20Integration-blue)]()
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

A hands-on laboratory designed to introduce the core concepts of **GitHub Actions** by building Continuous Integration (CI) workflows from scratch.

This project is intended for students, DevOps engineers, DevSecOps practitioners, and cybersecurity professionals who want to understand how GitHub Actions works before implementing advanced CI/CD and security automation pipelines.

---

# Objectives

By completing this lab, you will learn how to:

- Create your first GitHub Actions workflow
- Understand workflow triggers (events)
- Learn how GitHub-hosted runners work
- Execute shell commands inside workflows
- Organize jobs and steps
- Read workflow execution logs
- Understand the workflow lifecycle
- Build a solid foundation for future DevSecOps pipelines

---

# Technologies Used

| Technology | Purpose |
|------------|---------|
| GitHub Actions | Continuous Integration |
| YAML | Workflow definition |
| Ubuntu Runner | Execution environment |
| Bash | Command execution |
| Git | Version control |

---

# Repository Structure

```text
github-actions-fundamentals/
│
├── .github/
│   └── workflows/
│       └── basic-pipeline.yml
│
├── docs/
│   ├── architecture.md
│   ├── github-actions.md
│   ├── workflow-explained.md
│   └── screenshots/
│
├── scripts/
│
├── LICENSE
├── SECURITY.md
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── README.md
└── .gitignore
```

---

# Workflow Architecture

```
Developer Push
        │
        ▼
 GitHub Repository
        │
        ▼
 Workflow Trigger
        │
        ▼
 GitHub Runner
        │
        ▼
 Execute Steps
        │
        ▼
 Display Results
```

---

# Getting Started

## Clone the repository

```bash
git clone https://github.com/yourusername/github-actions-fundamentals.git

cd github-actions-fundamentals
```

## Trigger the workflow

The workflow executes automatically every time code is pushed to the `main` branch.

Simply modify a file and push your changes.

```bash
git add .

git commit -m "Run GitHub Actions workflow"

git push origin main
```

---

# Current Workflow

The current workflow demonstrates:

- Repository checkout
- Display current date
- Display current user
- Display operating system information
- Display Python version
- Create a temporary file
- List repository contents
- Finish successfully

---

# Expected Results

After each push:

- The workflow starts automatically.
- A GitHub-hosted Ubuntu runner is provisioned.
- Every configured step executes sequentially.
- The workflow finishes successfully.
- Logs are available under the **Actions** tab.

---

# Learning Path

This repository follows a progressive learning approach.

- Module 1 – Introduction to GitHub Actions
- Module 2 – Workflows
- Module 3 – Jobs and Steps
- Module 4 – GitHub Runners
- Module 5 – Variables
- Module 6 – Artifacts
- Module 7 – Conditional Execution
- Module 8 – Best Practices

---

# Documentation

Additional documentation is available in the `docs/` directory.

| Document | Description |
|----------|-------------|
| architecture.md | Workflow architecture |
| github-actions.md | GitHub Actions fundamentals |
| workflow-explained.md | Line-by-line workflow explanation |

---

# Screenshots

Workflow execution screenshots will be added after completing each module.

```
docs/screenshots/
```

---

# Future Improvements

Some planned enhancements include:

- Environment variables
- Workflow artifacts
- Conditional execution
- Matrix builds
- Caching
- Manual workflow dispatch
- Scheduled workflows
- Reusable workflows

---

# Contributing

Contributions, improvements, and suggestions are welcome.

Please read the `CONTRIBUTING.md` guide before submitting a pull request.

---

# License

This project is licensed under the MIT License.

---

# Author

**Roberto Delgado**

Senior Cybersecurity Consultant

Passionate about Cybersecurity, DevSecOps, Cloud Security, and Secure Software Development.
