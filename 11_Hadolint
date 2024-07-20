## 1. what is hadolint
Hadolint is a Dockerfile linter that helps you build best practice Docker images by detecting common mistakes and suggesting improvements.

## 2.Features

- Supports the Dockerfile syntax.
- Detects issues such as invalid syntax, insecure commands, and bad practices.
- Provides suggestions and best practices.
- Integrates with CI/CD pipelines.
- Extensible and customizable.

## 3.Usage

Hadolint can be run from the command line or integrated into your CI/CD pipeline.

To lint a Dockerfile, use the following command:


```bash
hadolint Dockerfile
```
If you are using the Docker container, you can run:

```bash
docker run --rm -i hadolint/hadolint < Dockerfile
```
CI/CD Integration,Create a file .github/workflows/hadolint.yml:

```bash
name: Lint Dockerfile

on: [push, pull_request]

jobs:
  hadolint:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout code
      uses: actions/checkout@v2
    - name: Run Hadolint
      uses: hadolint/hadolint-action@v1
      with:
        dockerfile: Dockerfile

```

## 4. Common Rules

- DL3000: Use absolute WORKDIR.
- DL3001: For some bash commands it makes no sense to use &&.
- DL3003: Use WORKDIR to switch to a directory.
- DL3006: Use SHELL to change the default shell.
- DL3008: Pin versions in apt-get install.
- DL3018: Pin versions in npm install.
- DL3020: Use COPY instead of ADD for files and folders.


Hadolint is a powerful tool for ensuring your Dockerfiles adhere to best practices and are free from common mistakes. 
By integrating Hadolint into your development workflow, you can create more secure and efficient Docker images.
