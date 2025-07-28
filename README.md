# 🛡️ Trivy Baseline Diff in CI/CD

This project demonstrates how to **automatically store baseline vulnerability scan results** using [Trivy](https://github.com/aquasecurity/trivy) and **compare against future scans** to reduce noise and avoid false positives in a real-world CI/CD pipeline.

> ✅ Focus: A practical approach to suppressing known issues and highlighting only new or regressed vulnerabilities.

---

## 📦 What’s Inside

- A simple **Node.js** application
- A **Dockerfile** for containerization
- A GitHub Actions workflow that:
  - Builds a container
  - Scans it with Trivy
  - Saves a baseline scan (`trivy-results.json`)
  - Compares future scans against the saved baseline using `--diff`

---

## ⚙️ GitHub Actions Workflow

Located in: `.github/workflows/trivy.yml`

### 🔁 On every push or PR:
1. Builds the image (`myapp:latest`)
2. Scans it with Trivy:
   ```bash
   trivy image --format json -o trivy-results.json myapp:latest
