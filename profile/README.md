# Hi there 👋 Welcome to Coffee Shop

[![Kubernetes](https://img.shields.io/badge/kubernetes-1.23+-326CE5?style=flat&logo=kubernetes&logoColor=white)](https://kubernetes.io/)
[![Helm](https://img.shields.io/badge/helm-3.8+-0F1689?style=flat&logo=helm&logoColor=white)](https://helm.sh/)
[![Docker](https://img.shields.io/badge/docker-latest-2496ED?style=flat&logo=docker&logoColor=white)](https://www.docker.com/)
[![Minikube](https://img.shields.io/badge/minikube-1.25+-326CE5?style=flat&logo=kubernetes&logoColor=white)](https://minikube.sigs.k8s.io/)

---

## Overview

**SADMS** is a comprehensive microservices platform showcasing modern distributed system design patterns including:

- **Microservices Architecture** - 10+ loosely coupled services with clear boundaries
- **Event-Driven Communication** - Kafka-based event streaming and saga orchestration
- **Cloud-Native Deployment** - Kubernetes with Helm charts, StatefulSets, and persistent storage
- **Polyglot Implementation** - Java (Spring Boot), python, Node.js, React, with gRPC and REST APIs
- **Distributed Data Management** - 5 MySQL databases + MongoDB with eventual consistency
- **Real-time Updates** - WebSocket notifications and live order tracking
- **Saga Pattern** - Choreography-based order orchestration with compensating transactions

---

## Project Structure
![img](https://cdn.jsdelivr.net/gh/leungll/MyImgHosting/img/Coffee-Shop-Architecture-New.png)

---

## Technology Stack

### Backend Services

- **Java**: Spring Boot 2.7+, Spring Cloud Gateway, Hibernate ORM
- **Node.js**: Express, gRPC, WebSocket (Socket.io)
- **Frameworks**: Eventuate (Saga), Spring Data JPA

### Frontend

- **React**: Modern SPA with functional components
- **Build Tools**: Vite, npm
- **Deployment**: nginx serving static assets

### Data Layer

- **MySQL 8.0**: User, Auth, Employee, Banking, Orchestrator databases
- **MongoDB**: Inventory document store
- **Persistence**: Kubernetes PersistentVolumes (35 GiB total)

### Infrastructure

- **Orchestration**: Kubernetes 1.23+ (Minikube for local)
- **Package Manager**: Helm 3.8+ charts
- **Messaging**: Apache Kafka, Apache Zookeeper, RabbitMQ
- **Containerization**: Docker, Docker Hub registry
- **CI/CD**: GitHub Actions (automated builds)

---

## Quick Start

### Prerequisites

- **Hardware**: 4+ CPU cores, 8GB+ RAM, 20GB+ disk
- **Software**: Docker Desktop, Minikube, kubectl, Helm

### Installation

```bash
# Clone repository
git clone https://github.com/18653-microservices/sadms-infra.git
cd sadms-infra

# Install required tools (macOS/Linux)
make install-tools

# Start Minikube cluster
make start

# Deploy entire SADMS stack
make deploy

# Verify deployment (wait ~10 minutes for all services)
make verify
```

### Access Applications

```bash
# Employee Portal, Login: alice / 1a2b3c
# Customer Portal, Create new account via signup
make setup-access

# View system status
make status
```

---

## Project Structure

```
sadms/
├── sadms-infra/              # Kubernetes/Helm deployment
│   ├── charts/sadms/         # Helm chart templates
│   ├── scripts/              # Deployment automation
│   ├── Makefile              # All operational commands
│   └── README.md             # Comprehensive documentation
│
├── Backend Services/
│   ├── sadms-gateway/        # Gateway (Node.js)
│   ├── sadms-user/           # User management (Spring Boot)
│   ├── sadms-auth/           # Authentication (Spring Boot)
│   ├── sadms-employee/       # Employee management (Spring Boot)
│   ├── sadms-menu/           # Product catalog (Node.js)
│   ├── sadms-inventory/      # Stock tracking (Node.js + MongoDB)
│   ├── sadms-mypay/          # Payments (Spring Boot)
│   ├── sadms-banking/        # Finance (Spring Boot)
│   ├── sadms-notification/   # Real-time alerts (Node.js + WebSocket)
│   ├── sadms-buyer/          # Auto-purchasing (Spring Boot)
│   └── sadms-mq-switch/      # Message routing (Node.js)
│
└── Frontend Applications/
    ├── sadms-frontend/           # Customer portal (React)
    ├── sadms-frontend-employee/  # Employee portal (React)
    └── sadms-mq-dashboard/       # MQ monitoring (React)
```

---

## Development Workflow

### Daily Operations

```bash
# Start your day
make start              # Resume cluster (30-60s)
make status             # Verify services

# During development
make upgrade SERVICE=menu     # Update specific service
make logs SERVICE=menu        # View logs

# End your day
make stop               # Preserve all data
```

### Service Updates

When code changes are pushed, GitHub Actions automatically builds and pushes new Docker images:

```bash
# Update single service
kubectl rollout restart deployment/sadms-menu -n sadms

# Update all services
make upgrade

# Monitor rollout
kubectl rollout status deployment/sadms-menu -n sadms
```

### Debugging

```bash
# View pods
kubectl get pods -n sadms

# Check logs
kubectl logs -f deployment/sadms-gateway -n sadms

# Shell access
kubectl exec -it <pod-name> -n sadms -- /bin/bash

# Database access
kubectl exec -it sadms-user-db-0 -n sadms -- mysql -uroot -ppassword

# Recent events
kubectl get events -n sadms --sort-by='.lastTimestamp'
```

---

## Documentation

- **[sadms-infra/README.md](https://github.com/18653-microservices/sadms-infra/blob/main/README.md)** - Complete infrastructure guide
- **[sadms-infra/QUICKSTART.md](https://github.com/18653-microservices/sadms-infra/blob/main/QUICKSTART.md)** - 5-minute setup
- **[sadms-infra/LIFECYCLE.md](https://github.com/18653-microservices/sadms-infra/blob/main/LIFECYCLE.md)** - Lifecycle management

---

## Contributing

Each service has its own repository with:
- Service-specific README
- API documentation
- Unit and integration tests
- Dockerfile for containerization

### Build Pipeline

1. Code pushed to service repository
2. GitHub Actions triggers build
3. Docker image built and tagged
4. Image pushed to Docker Hub (`cmusv/*`)
5. Deploy to Kubernetes: `make upgrade SERVICE=<name>`

---

## System Requirements

| Resource | Minimum | Recommended |
|----------|---------|-------------|
| CPU | 4 cores | 8 cores |
| RAM | 8 GB | 16 GB |
| Disk | 20 GB | 50 GB |
| OS | macOS, Linux, Windows (WSL2) | - |

