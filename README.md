# Jenkins Pipeline Project

This is a Python repository managed by Poetry
This repository contains 2 Jenkins pipelines designed for CI/CD automation.
Jenkinsfile is intended to detect version change based on the Poetry configuration file (pyproject.toml)
JenkinsfileTAG is intended to detect version change based on GitHub tag/release creation

---

## Project Structure

This project has got multiple files and directories and each directory has its own purpose.
The root directory contains configuration files (like pyproject.toml) and CI/CD files like Jenkinsfile.
(There is also the gitignore file, the README file and the LICENSE file in the root directory.)
The "src" directory is the place where devs store the application code.
The "test" directory is where devs/testers store the tests code.

---

## 🛠 Requirements

- Jenkins v2.277+ with Pipeline, Git, GitHub plugins
- Agent machine with necessary tools installed (e.g., Docker, Node.js, Java, etc.)
- GitHub credentials or tokens configured in Jenkins credentials store

---

## Jenkins configuration

- my trigger - the pipeline job which points to this repository (via Git plugin) and uses the Jenkinsfile; it is automatically executed once commit happens in this remote repository.
- my tag trigger - the pipeline job which points to this repository (via Git plugin) and uses the Jenkinsfile; it is automatically executed once a tag is created in this remote repository.

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
2. Create a new Jenkins job and point it to this repository (and pipeline filename).
3. Configure required credentials and environment variables in Jenkins.
4. Trigger the pipeline manually or set up GitHub hooks or the Jenkins Polling mechanism for automatic execution.

---

## Customization

- Edit the `Jenkinsfile` or `JenkinsfileTAG` to adjust pipeline stages/behaviour.
- Modify version in `pyproject.toml` to test the detection feature.
- Adjust pipeline triggers, timeouts, or error handling to suit your workflow.

---
