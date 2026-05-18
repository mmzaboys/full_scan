# full_scan

## How To Use The Composite Actions

```yaml
name: Security

on:
  pull_request:
  push:
    branches:
      - main

jobs:
  security:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Repository
        uses: actions/checkout@v4

      # -------------------------
      # IaC Scan
      # -------------------------
      - name: Run IaC Scan
        uses: ORG/Repository_name/actions/iac@main
        with:
          iac_Path: .

      # -------------------------
      # SAST Scan
      # -------------------------
      - name: Run SAST Scan
        uses: ORG/Repository_name/actions/sast@main
        with:
          source_code_path: .

      # -------------------------
      # Container Scan
      # -------------------------
      - name: Run Container Scan
        uses: ORG/Repository_name/actions/containeScan@main
        with:
          image_name: myapp:latest
          REPO_USER: ${{ secrets.REPO_USER }}
          REPO_PWD: ${{ secrets.REPO_PWD }}
```