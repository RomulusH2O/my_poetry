# Jenkins Pipeline Project

This repository contains 2 Jenkins pipelines designed for CI/CD automation.
Jenkinsfile is intended to detect version change based on the Poetry configuration file (pyproject.toml)
JenkinsfileTAG is intended to detect version change based on GitHub tag/release creation

---

## Project Structure

---

## Requirements

- Jenkins v2.277+ with Pipeline plugin
- Agent machine with necessary tools installed (e.g., Docker, Node.js, Java, etc.)
- GitHub credentials or tokens configured in Jenkins credentials store

---

## Jenkinsfile Overview

This pipeline is meant to automatically detect version change on GitHub repository
The pipeline is structured into the following stages:

1. **Poll** – Trigger the pipeline when project version is created (pyproject.toml)
2. **Checkout** – Get source code changes from Git repository
3. **Compare** – Run SemVer comparison algorithms
4. **Info** – Tell the version changes

## JenkinsfileTAG Overview

This pipeline is meant to automatically detect GitHub repository tags
The pipeline is structured into the following stages:

1. **Poll** – Trigger the pipeline when a tag is created
2. **Checkout** – Get source code changes from Git repository
3. **Compare** – Run SemVer comparison algorithms
4. **Info** – Tell the version changes

---

## Usage

1. Fork this repository and modify the `Jenkinsfile` or `JenkinsfileTAG` as needed.
2. Create a new Jenkins job and point it to your repository.
3. Configure required credentials and environment variables in Jenkins.
4. Trigger the pipeline manually or set up Git hooks for automatic execution.

---

## Customization

- Edit the `Jenkinsfile` or `JenkinsfileTAG` to adjust pipeline stages/behaviour.
- Modify version in `pyproject.toml` to test the detection feature.
- Adjust pipeline triggers, timeouts, or error handling to suit your workflow.

---
