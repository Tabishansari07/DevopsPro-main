# devops-cicd-demo

A Spring Boot application with a fully automated CI/CD pipeline using **GitHub Actions**, **Maven**, and **Docker**.

## Pipeline Overview

Every `git push` to `main` automatically:

1. **Builds & Tests** — Maven compiles the app and runs JUnit 5 unit tests
2. **Dockerizes** — Builds a multi-stage Docker image and pushes to Docker Hub
3. **Verifies** — Pulls the image, runs the container, and checks the `/health` endpoint

## Tech Stack

| Tool | Role |
|---|---|
| Spring Boot 3.2 | Java web application |
| Maven 3.9 | Build automation & dependency management |
| Docker | Containerization (multi-stage build) |
| GitHub Actions | CI/CD pipeline automation |
| Docker Hub | Container image registry |

## Run Locally

```bash
docker pull <dockerhub-username>/devops-cicd-demo:latest
docker run -p 8080:8080 <dockerhub-username>/devops-cicd-demo:latest
curl http://localhost:8080/health
```

## Project Structure

```
├── app/
│   ├── src/               # Spring Boot source & tests
│   ├── Dockerfile         # Multi-stage container build
│   └── pom.xml            # Maven configuration
└── .github/workflows/
    └── docker-publish.yml # CI/CD pipeline definition
```

