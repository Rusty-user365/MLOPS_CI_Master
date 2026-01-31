# MLOPS_CI_Master


This project is to demonstrate an end to end implementation of Continuous Integration.


# Continuous Integration (CI) Tutorial ⚡

This guide shows how to set up a basic CI pipeline using GitHub Actions.

## What is CI?
Continuous Integration (CI) automatically builds and tests your code whenever you push changes.  
It helps catch errors early and ensures your project stays stable.

---

## 1. Create Workflow File
Inside your repo, add a file at:
```
.github/workflows/ci.yaml
```

## 2. Example CI Workflow
```yaml
name: CI Pipeline

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      # Checkout code
      - name: Checkout repository
        uses: actions/checkout@v3

      # Setup Python (example project)
      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.9'

      # Install dependencies
      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          pip install -r requirements.txt

      # Run tests
      - name: Run tests
        run: |
          pytest
```

---

## 3. How It Works
- **Trigger**: Runs on every push or pull request to `main`.
- **Environment**: Uses Ubuntu runner with Python 3.9.
- **Steps**:
  1. Checkout code  
  2. Install dependencies  
  3. Run tests with `pytest`

---
