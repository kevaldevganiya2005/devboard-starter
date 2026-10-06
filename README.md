# DevBoard — Full-Stack DevOps Project

DevBoard is a full-stack task management application built with React, Go and PostgreSQL.

I use this project to practice real-world DevOps concepts including Docker, Jenkins CI, Docker Hub and Kubernetes.

## Architecture

GitHub
  |
  v
Jenkins CI
  |
  +-- Backend Tests
  +-- Frontend Build
  +-- Docker Build
          |
          v
      Docker Hub
          |
          v
     Kubernetes
      /   |   \
 Frontend Backend PostgreSQL
    |       |       |
 Service  Service   PVC
      \    |      /
        Ingress

## Tech Stack

### Application
- React
- Vite
- Go
- PostgreSQL

### DevOps
- Git
- GitHub
- Docker
- Docker Compose
- Docker Hub
- Jenkins
- Kubernetes
- Kind
- NGINX Ingress

## Project Structure

- backend/ — Go backend API
- frontend/ — React frontend
- k8s/ — Kubernetes manifests
- Jenkinsfile — Jenkins CI pipeline
- docker-compose.yml — local container setup
- README.md — project documentation

## Docker

Docker images:

- kevaldevganiya2005/devboard-backend:latest
- kevaldevganiya2005/devboard-frontend:latest

The application can also be run locally using Docker Compose.

## Jenkins CI

Jenkins automates the CI pipeline:

Checkout
  |
Backend Tests
  |
Frontend Build
  |
Docker Build
  |
Docker Image Verification
  |
Docker Hub Push

## Kubernetes

The application is deployed on a Kind Kubernetes cluster.

Kubernetes resources used:

- Namespace
- Deployment
- Service
- Secret
- PersistentVolumeClaim
- Ingress
- Readiness Probe
- Liveness Probe
- Resource Requests and Limits
- RollingUpdate

## PostgreSQL

PostgreSQL runs inside Kubernetes and uses a PersistentVolumeClaim for persistent storage.

The backend connects to PostgreSQL through the Kubernetes Service:

postgres:5432

## Health Checks

Backend health endpoint:

GET /health

Example response:

{"service":"backend","status":"ok"}

Kubernetes uses this endpoint for readiness and liveness probes.

## Configuration and Secrets

Database connection information is provided to the backend through Kubernetes Secrets.

Sensitive database credentials are not committed directly into application source code.

## DevOps Concepts Practiced

- Git and GitHub
- Docker
- Docker Compose
- Docker Hub
- Jenkins CI
- Docker image build and push
- Kubernetes Deployments
- Kubernetes Services
- Kubernetes Secrets
- PersistentVolumeClaim
- Ingress
- Health probes
- Resource requests and limits
- Rolling Updates
- Kubernetes networking
- Service discovery
- PostgreSQL persistence
- Kubernetes troubleshooting

## Current Status

### Completed

- Full-stack application
- Dockerized frontend and backend
- Docker Compose
- Jenkins CI pipeline
- Docker Hub image publishing
- Kubernetes deployment
- PostgreSQL persistence
- Health probes
- Resource management
- Kubernetes Services
- Ingress configuration

### Planned

- Jenkins to Kubernetes Continuous Deployment
- Automated Kubernetes deployments
- HPA
- Prometheus
- Grafana
- Centralized logging
- Cloud deployment

## DevOps Workflow

Code
  |
GitHub
  |
Jenkins
  |
Tests
  |
Docker Build
  |
Docker Hub
  |
Kubernetes
  |
Application

## Author

Keval Devganiya

GitHub:
https://github.com/kevaldevganiya2005

---

This project is part of my journey with strong DevOps and Cloud skills.
