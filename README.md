# Android Mobile CI/CD Pipeline (GitHub Actions + Fastlane + Firebase + SonarCloud)

This repository demonstrates a production-style CI/CD pipeline for Android applications using:

- GitHub Actions
- Fastlane
- Firebase App Distribution
- SonarCloud
- Gradle
- PR-based workflow

It is designed to simulate how mobile DevOps pipelines are implemented in enterprise environments.

---

## 🚀 Workflow Overview

Developer → Pull Request → CI → Manual Approval → CD → Firebase Distribution

### Pipeline Stages

1. Developer pushes code to a feature branch
2. Pull Request is created
3. CI pipeline runs (Build / Optional Tests / SonarCloud Scan)
4. PR is reviewed and merged
5. CD pipeline is manually triggered
6. APK is distributed via Firebase App Distribution

---

## 📂 Main Workflow File

```
.github/workflows/android-ci.yml
```

This file contains both CI and CD stages with manual controls.

---

## ⚙️ CI/CD Architecture

### CI Stage (Build & Quality)

Runs on:
- Pull Requests
- Manual trigger

Responsibilities:
- Checkout source code
- Setup Java & Android SDK
- Build APK using Gradle
- (Optional) Run unit tests
- Run SonarCloud analysis

### CD Stage (Distribution)

Runs on:
- Manual trigger only

Responsibilities:
- Build APK
- Upload to Firebase App Distribution using Fastlane
- Notify testers

---

## 🔐 Required Secrets

The following secrets must be configured in GitHub:

Path:
Settings → Secrets and variables → Actions → Secrets

| Name          | Description                          |
|---------------|--------------------------------------|
| FIREBASE_TOKEN| Firebase CLI token for CI upload     |
| SONAR_TOKEN   | SonarCloud project token             |

---

## 🧪 SonarCloud Integration

This pipeline integrates SonarCloud for:

- Static code analysis
- Security checks
- Code smells
- Maintainability metrics

SonarCloud runs during CI and reports quality results on:

- Pull Requests
- Main branch

Dashboard:
https://sonarcloud.io

---

## 📦 Artifact Management

This pipeline manages Android build artifacts:

| Type | Description |
|------|-------------|
| APK  | Debug build for testing |
| AAB  | (Optional) Play Store bundle |
| dSYM | (iOS equivalent - future ready) |

Artifacts are generated using Gradle and handled by Fastlane.

---

## 📱 Mobile Distribution

Firebase App Distribution is used to:

- Upload APKs
- Manage testers
- Distribute builds
- Track releases

Distribution is automated via Fastlane.

---

## 🔄 Branching Strategy

This project follows a PR-based workflow.

### Branch Types

- main → Production-ready code
- feature/* → Development branches

### Flow

1. Create feature branch
2. Push changes
3. Open PR
4. CI runs
5. Review
6. Merge
7. Manual CD

---

## ▶️ How to Simulate a PR

### Step 1 — Create Branch

```
git checkout -b feature/demo
```

### Step 2 — Push

```
git push origin feature/demo
```

### Step 3 — Open PR

Open GitHub → Create Pull Request → feature/demo → main

CI will run automatically.

---

## ▶️ How to Run CD Manually

1. Go to GitHub → Actions
2. Select "Android CI/CD"
3. Click "Run workflow"
4. Enable CD option
5. Start workflow

This prevents accidental releases.

---

## 📊 Monitoring & Observability

Integrated tools:

- SonarCloud → Code Quality
- GitHub Actions → Pipeline Logs
- Firebase Console → Distribution

This enables traceability from commit → release.

---

## 🔒 Security & Compliance

Security practices implemented:

- Secrets stored in GitHub Vault
- Token-based authentication
- PR-based approvals
- Static analysis
- Controlled deployments

---

## 🛠️ Technologies Used

| Category | Tools |
|----------|--------|
| CI/CD | GitHub Actions |
| Build | Gradle |
| Automation | Fastlane |
| Distribution | Firebase App Distribution |
| Quality | SonarCloud |
| SCM | GitHub |
| Language | Kotlin / Java |

---

## 🎯 Project Objectives

This project demonstrates:

- Enterprise-style mobile CI/CD
- Secure artifact handling
- Quality gates
- Manual release controls
- DevOps best practices
- Automation at scale

It is designed for technical interviews and portfolio presentation.

---

## 📌 Future Improvements

Planned enhancements:

- AAB support
- Play Store deployment
- iOS pipeline
- Jenkins migration
- Kubernetes runners
- Nexus integration
- SAST/DAST tools

---

## 👤 Author

Mark Amir  
Senior DevOps / SaaSOps Engineer  

Specialized in:
- Cloud Infrastructure
- Kubernetes
- CI/CD
- Mobile DevOps
- Observability
- Automation

---

## 📄 License

MIT License
