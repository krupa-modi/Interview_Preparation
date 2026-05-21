# CI/CD Complete Guide (Interview + Real Project)

# What is CI/CD?

CI/CD software development ka modern process hai jo:
- code testing
- building
- deployment

ko automatic bana deta hai.

---

# Full Form

| Short Form | Full Form |
|---|---|
| CI | Continuous Integration |
| CD | Continuous Delivery / Continuous Deployment |

---

# Simple Definition

## CI

Developers ka code automatically:
- test
- build
- merge

hota hai.

---

## CD

Tested code automatically:
- server par deploy

hota hai.

---

# Real Life Example

```text id="v4k8qn"
Developer Code Push
        ↓
Automatic Testing
        ↓
Build Application
        ↓
Deploy to Server
````

Ye pura automation:

* CI/CD pipeline

kehlata hai.

---

# Why CI/CD is Used?

Without CI/CD:

```text id="y7m3td"
Manual Testing
Manual Build
Manual Deployment
More Errors
Slow Release
```

With CI/CD:

```text id="t8q5zn"
Automatic Testing
Automatic Deployment
Fast Release
Less Bugs
```

---

# Main Goals of CI/CD

| Goal               | Meaning          |
| ------------------ | ---------------- |
| Automation         | Manual work kam  |
| Faster Delivery    | Fast deployment  |
| Better Quality     | Bugs kam         |
| Team Collaboration | Easy integration |
| Continuous Release | Frequent updates |

---

# What is Continuous Integration (CI)?

Developers daily code push karte hai.

CI automatically:

* code merge
* testing
* build verification

karta hai.

---

# CI Flow

```text id="u3r8yb"
Developer Push Code
        ↓
GitHub/GitLab
        ↓
Run Tests
        ↓
Build Project
        ↓
Check Errors
        ↓
Merge Code
```

---

# What Happens in CI?

| Task                 | Description   |
| -------------------- | ------------- |
| Install Dependencies | npm install   |
| Run Tests            | unit testing  |
| Run Linter           | ESLint        |
| Build App            | npm run build |
| Check Errors         | validation    |

---

# What is Continuous Delivery (CD)?

Code production-ready automatically ban jata hai.

Deployment manually trigger hota hai.

---

# Continuous Deployment

Code automatically production server par deploy bhi ho jata hai.

---

# Difference Between Delivery and Deployment

| Delivery             | Deployment        |
| -------------------- | ----------------- |
| Manual deploy        | Automatic deploy  |
| Ready for production | Direct production |
| Human approval       | No approval       |


* Continuous Delivery me application automatically production-ready hoti hai but deployment manually trigger hota hai.

* Continuous Deployment me deployment bhi automatically production me ho jata hai without manual approval.

One Line Difference
 * Delivery = Manual Deploy(pehle staging pe than manaual approval ke bad production pe)
 * Deployment = Automatic Deploy(automatically production pe deployement hota hai test pass hua to)
---

# CI/CD Pipeline

## What is Pipeline?

Pipeline automation steps ka sequence hota hai.

---

# Pipeline Steps

```text id="d6v1qf"
1. Code Push
2. Install Dependencies
3. Run Tests
4. Build Project
5. Deploy Application
6. Monitor
```

---

# Most Popular CI/CD Tools

| Tool                | Use               |
| ------------------- | ----------------- |
| Jenkins             | Automation server |
| GitHub Actions      | GitHub CI/CD      |
| GitLab CI/CD        | GitLab pipeline   |
| CircleCI            | Cloud CI/CD       |
| Travis CI           | Testing pipeline  |
| Azure DevOps        | Microsoft CI/CD   |
| Bitbucket Pipelines | Atlassian CI/CD   |

---

# Most Used Modern Tool

```text id="q2n8xr"
GitHub Actions
```

---

# CI/CD Architecture

```text id="m9k3tv"
Developer
   ↓
Git Push
   ↓
Repository (GitHub)
   ↓
CI/CD Tool
   ↓
Testing
   ↓
Build
   ↓
Deploy
   ↓
Production Server
```

---

# Real React Project CI/CD Flow

```text id="r5x7jn"
Developer writes React code
        ↓
Push code to GitHub
        ↓
GitHub Actions runs
        ↓
npm install
        ↓
npm run test
        ↓
npm run build
        ↓
Deploy to Vercel/AWS/Netlify
```

---

# GitHub Actions

# What is GitHub Actions?

GitHub ka built-in CI/CD tool.

Automatically workflows run karta hai.

---

# GitHub Actions Folder

```text id="f7n2mp"
.github/workflows/
```

---

# Example CI/CD File

# main.yml

```yaml id="n3q8wd"
name: React CI/CD

on:
  push:
    branches:
      - main

jobs:

  build:

    runs-on: ubuntu-latest

    steps:

      - name: Checkout Code
        uses: actions/checkout@v3

      - name: Install Node.js
        uses: actions/setup-node@v3
        with:
          node-version: 18

      - name: Install Dependencies
        run: npm install

      - name: Run Tests
        run: npm test

      - name: Build Project
        run: npm run build
```

---

# Explanation

## on

```yaml id="e6r4pk"
on:
  push:
```

Push hone par workflow run karega.

---

# jobs

Workflow tasks.

---

# runs-on

OS environment.

```yaml id="s8t1vy"
ubuntu-latest
```

---

# steps

Execution steps.

---

# actions/checkout

Repository code fetch karta hai.

---

# npm install

Dependencies install karta hai.

---

# npm test

Testing run karta hai.

---

# npm run build

Production build create karta hai.

---

# Deployment Example (Netlify/Vercel)

## Automatic Deployment

Code push → auto deploy.

---

# Deployment Platforms

| Platform | Use                |
| -------- | ------------------ |
| Vercel   | React/Next.js      |
| Netlify  | Frontend apps      |
| AWS      | Enterprise hosting |
| Firebase | Hosting            |
| Heroku   | Backend deployment |

---

# CI/CD in React

## React Projects me Common Steps

```text id="w6m9zp"
npm install
npm run lint
npm run test
npm run build
deploy
```

---

# Important Concepts

# 1. Build

Production optimized app create karna.

```bash id="v2q7rd"
npm run build
```

---

# 2. Testing

Application verify karna.

---

# 3. Linting

Code quality check.

Example:

```bash id="x8m3yc"
npm run lint
```

---

# 4. Deployment

Server par application upload karna.

---

# 5. Automation

Manual kaam ko automatic banana.

---

# Environments

| Environment | Purpose         |
| ----------- | --------------- |
| Development | Developer work  |
| Testing     | QA testing      |
| Staging     | Production-like |
| Production  | Live app        |

---

# CI/CD Benefits

| Benefit              | Description      |
| -------------------- | ---------------- |
| Faster Release       | Fast deployment  |
| Less Human Error     | Automation       |
| Better Code Quality  | Automated tests  |
| Easy Rollback        | Previous version |
| Better Collaboration | Team integration |

---

# Problems Without CI/CD

| Problem           | Description       |
| ----------------- | ----------------- |
| Manual deployment | Time waste        |
| More bugs         | No testing        |
| Slow release      | Delay             |
| Merge conflicts   | Integration issue |

---

# Real Company Workflow

```text id="h4v2qb"
Developer Branch
      ↓
Pull Request
      ↓
CI Tests Run
      ↓
Code Review
      ↓
Merge to Main
      ↓
CD Deploy
```

---

# CI/CD with Docker

Docker containerize application karta hai.

Pipeline me:

* build image
* push image
* deploy container

hota hai.

---

# CI/CD with Kubernetes

Kubernetes:

* scaling
* deployment
* orchestration

handle karta hai.

Large companies use:

* Docker + Kubernetes + CI/CD

---

# Security in CI/CD

| Security Practice     | Description         |
| --------------------- | ------------------- |
| Secret Variables      | API keys secure     |
| Environment Variables | Hidden configs      |
| Access Control        | Limited access      |
| Automated Scans       | Vulnerability check |

---

# Common Interview Questions

# What is CI/CD?

CI/CD software development process hai jo testing aur deployment automate karta hai.

---

# Difference Between CI and CD?

| CI               | CD             |
| ---------------- | -------------- |
| Code integration | Deployment     |
| Testing/build    | Release/deploy |

---

# What is Pipeline?

Automation steps ka sequence.

---

# What is GitHub Actions?

GitHub ka built-in CI/CD automation tool.

---

# Why CI/CD Important?

* Fast delivery
* Less bugs
* Automation
* Better quality

---

# What happens after code push?

```text id="u7k1fp"
Code Push
↓
Pipeline Trigger
↓
Testing
↓
Build
↓
Deploy
```

---

# What is Build?

Production-ready optimized files create karna.

---

# What is Deployment?

Application ko server par host karna.

---

# What is Staging Environment?

Production jaisa testing environment.

---

# Real Interview Answer

CI/CD ek automated software development process hai jo code integration, testing aur deployment ko automate karta hai taaki fast aur reliable releases ho sake.

---

# One Line Definition

CI/CD software delivery process ko automate karta hai.

---

# Easy Short Notes

| Keyword        | Meaning                        |
| -------------- | ------------------------------ |
| CI             | Continuous Integration         |
| CD             | Continuous Delivery/Deployment |
| Pipeline       | Automation steps               |
| Build          | Production files               |
| Deploy         | Server upload                  |
| GitHub Actions | CI/CD tool                     |
| Automation     | Manual work remove             |

---

# Most Important Commands

```bash id="k5p9wx"
npm install
npm test
npm run build
npm run lint
```

---

# Final Flow

```text id="n1v6mk"
Write Code
   ↓
Push to GitHub
   ↓
CI Runs
   ↓
Tests Pass
   ↓
Build Project
   ↓
CD Deploys App
   ↓
Live Website
```


# Difference Between Jenkins, GitHub Actions, AWS and Kubernetes

Bahot log confuse ho jate hai ki:
- Jenkins
- GitHub Actions
- AWS
- Kubernetes

same hai kya?

Answer:

```text
NO
````

Ye sab alag alag tools/services hai aur different kaam karte hai.

---

# Simple Overview

| Tool           | Main Purpose              |
| -------------- | ------------------------- |
| Jenkins        | CI/CD Automation Tool     |
| GitHub Actions | GitHub ka CI/CD Tool      |
| AWS            | Cloud Platform            |
| Kubernetes     | Container Management Tool |

---

# 1. Jenkins

# What is Jenkins?

Jenkins ek:

* CI/CD automation server

hai.

Automation karta hai:

* testing
* build
* deployment

---

# Jenkins Main Work

```text id="p5n8vr"
Code Push
   ↓
Run Tests
   ↓
Build Project
   ↓
Deploy App
```

---

# Jenkins Features

| Feature     | Description         |
| ----------- | ------------------- |
| Open Source | Free                |
| Plugins     | Bahot plugins       |
| Automation  | CI/CD               |
| Flexible    | Highly customizable |

---

# Jenkins Example

```text id="y7m1qx"
GitHub se code lo
↓
npm install
↓
npm test
↓
npm build
↓
Deploy
```

---

# Jenkins Kaha Use Hota Hai?

* Enterprise companies
* Large projects
* Custom pipelines

---

# 2. GitHub Actions

# What is GitHub Actions?

GitHub ka built-in CI/CD tool.

---

# Main Purpose

Automation:

* testing
* build
* deployment

---

# GitHub Actions Flow

```text id="f4k9tp"
Code Push to GitHub
        ↓
Workflow Trigger
        ↓
Tests Run
        ↓
Build
        ↓
Deploy
```

---

# GitHub Actions Features

| Feature           | Description      |
| ----------------- | ---------------- |
| Built into GitHub | Extra setup kam  |
| YAML workflows    | Easy config      |
| Cloud based       | No server manage |
| Easy integration  | GitHub connected |

---

# GitHub Actions vs Jenkins

| Jenkins                | GitHub Actions  |
| ---------------------- | --------------- |
| Separate server needed | GitHub built-in |
| More setup             | Easy setup      |
| Highly customizable    | Easier          |
| Old & enterprise       | Modern & simple |

---

# Important

## Jenkins aur GitHub Actions dono:

```text id="n2v7qb"
CI/CD Tools
```

hai.

---

# 3. AWS

# What is AWS?

AWS = Amazon Web Services

Ye:

* cloud platform

hai.

---

# AWS Kya Karta Hai?

Provides:

* servers
* database
* hosting
* storage
* networking

---

# Example

React app ko:

* host
* deploy

karne ke liye AWS use kar sakte hai.

---

# AWS Services

| Service    | Use            |
| ---------- | -------------- |
| EC2        | Virtual Server |
| S3         | Storage        |
| RDS        | Database       |
| Lambda     | Serverless     |
| CloudFront | CDN            |

---

# Important

## AWS CI/CD tool nahi hai.

Ye:

* cloud infrastructure

provide karta hai.

---

# AWS Example

```text id="u6m3wr"
App Deploy on AWS Server
```

---

# 4. Kubernetes

# What is Kubernetes?

Kubernetes ek:

* container orchestration tool

hai.

Short form:

```text id="x8q1vk"
K8s
```

---

# Kubernetes Main Work

Docker containers ko:

* manage
* scale
* deploy
* monitor

karna.

---

# Kubernetes Example

Suppose:

* 1000 users app use kar rahe hai.

Kubernetes automatically:

* more containers create
* traffic manage

karega.

---

# Kubernetes Features

| Feature               | Description              |
| --------------------- | ------------------------ |
| Auto Scaling          | Traffic handle           |
| Load Balancing        | Request distribute       |
| Self Healing          | Failed container restart |
| Deployment Management | Container deployment     |

---

# Kubernetes Works With

```text id="v3p9mx"
Docker
```

---

# Important

## Kubernetes CI/CD tool nahi hai.

Ye:

* container management tool

hai.

---

# Real Flow (Industry)

```text id="r5n2qk"
Developer Push Code
        ↓
GitHub Actions / Jenkins
        ↓
Build Docker Image
        ↓
Deploy to AWS
        ↓
Kubernetes manages containers
```

---

# Very Important Difference

| Tool           | Type                    | Main Work              |
| -------------- | ----------------------- | ---------------------- |
| Jenkins        | CI/CD Tool              | Automation             |
| GitHub Actions | CI/CD Tool              | Automation             |
| AWS            | Cloud Platform          | Hosting/Infrastructure |
| Kubernetes     | Container Orchestration | Container management   |

---

# Real Life Analogy

| Tool                   | Analogy                    |
| ---------------------- | -------------------------- |
| Jenkins/GitHub Actions | Factory automation machine |
| AWS                    | Land/building/server       |
| Kubernetes             | Container manager          |

---

# Simple Relationship

```text id="k7v1px"
Jenkins/GitHub Actions
        ↓
Build & Deploy App
        ↓
AWS Server
        ↓
Kubernetes manages app containers
```

---

# Which One Should Frontend Developer Learn?

# Important for Frontend

| Priority     | Learn             |
| ------------ | ----------------- |
| High         | GitHub Actions    |
| Medium       | AWS basics        |
| Medium       | Docker basics     |
| Low/Optional | Kubernetes basics |
| Optional     | Jenkins basics    |

---

# Most Common Modern Stack

```text id="d4m8tn"
GitHub Actions
+
Docker
+
AWS
+
Kubernetes
```

---

# Interview Questions

# What is Jenkins?

Jenkins ek open-source CI/CD automation tool hai.

---

# What is GitHub Actions?

GitHub ka built-in CI/CD automation service.

---

# What is AWS?

AWS Amazon ka cloud computing platform hai.

---

# What is Kubernetes?

Kubernetes container orchestration tool hai jo Docker containers manage karta hai.

---

# Difference Between Jenkins and GitHub Actions?

| Jenkins        | GitHub Actions    |
| -------------- | ----------------- |
| Separate setup | GitHub integrated |
| More control   | Easier            |
| Plugin based   | YAML workflows    |

---

# Difference Between AWS and Kubernetes?

| AWS                    | Kubernetes         |
| ---------------------- | ------------------ |
| Cloud platform         | Container manager  |
| Infrastructure provide | Containers manage  |
| Hosting                | Scaling/deployment |

---

# One Line Definitions

## Jenkins

CI/CD automation tool.

---

## GitHub Actions

GitHub based CI/CD automation.

---

## AWS

Cloud infrastructure platform.

---

## Kubernetes

Container management system.




