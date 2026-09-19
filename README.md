# Microservices E-Commerce Platform

An end-to-end microservices e-commerce system used as a hands-on project to practice
production-style DevOps and DevSecOps workflows — from local containers to a GitOps
deployment on Kubernetes.

## Architecture
React client + 5 Java Spring Boot microservices:
- authentication-service
- common-data-service
- payment-service
- search-suggestion-service
- seller-account-service

Each service has its own multi-stage Dockerfile (dev/prod variants) and connects to MySQL.

## Tech stack
**App:** Java Spring Boot, React, MySQL
**CI/CD:** Jenkins (Shared Libraries), SonarQube, Nexus, Trivy, OWASP Dependency-Check
**Secrets:** HashiCorp Vault
**Infra:** Terraform (S3 backend + DynamoDB state locking)
**Orchestration:** Kubernetes (Minikube → EKS), ArgoCD (GitOps, separate manifests repo)
**Observability:** Prometheus, Grafana, ELK stack

## What I built and debugged
- Got `authentication-service` fully working end-to-end on EC2
- Fixed Docker build-context path bugs (COPY/ADD issues) blocking image builds
- Migrated all services off deprecated `openjdk`/`maven` base images to `eclipse-temurin`
- Traced and fixed environment-variable-driven DB configuration (`DB_HOST`, `DB_PORT`,
  `DB_SCHEMA`, `DB_USER`, `DB_PASS`) into a linked MySQL container
- Verified the full signup → authenticate → JWT flow using curl-based manual testing
- Set up Terraform state management with S3 + DynamoDB locking
- Integrated SonarQube, Trivy, and OWASP Dependency-Check into the Jenkins pipeline for
  code quality and vulnerability scanning

## Note on origin
This project started from a cloned reference repository to get realistic multi-service
complexity. The infrastructure, CI/CD pipeline, security tooling, and debugging above are
my own work built on top of it.

## How to run
[Add your actual run steps — Minikube setup, env vars needed, docker-compose or k8s manifests to apply, etc.]
