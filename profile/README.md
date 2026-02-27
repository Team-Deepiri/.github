<div align="center">

# Deepiri

An open source organization currently focused on building an **intelligence platform for building scalable AI-powered data ingestion and automated workflows.**
[![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)](#)
[![Python](https://img.shields.io/badge/Python-14354C?style=for-the-badge&logo=python&logoColor=white)](#)
[![Go](https://img.shields.io/badge/Go-00ADD8?style=for-the-badge&logo=go&logoColor=white)](#)
[![Kubernetes](https://img.shields.io/badge/kubernetes-%23326ce5.svg?style=for-the-badge&logo=kubernetes&logoColor=white)](#)
[![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)](#)
[![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB)](#)
[![PostgreSQL](https://img.shields.io/badge/postgresql-4169e1?style=for-the-badge&logo=postgresql&logoColor=white)](#)
[![Redis](https://img.shields.io/badge/redis-%23DD0031.svg?style=for-the-badge&logo=redis&logoColor=white)](#)

<br>

<img src="../assets/deepiri-logo.png" alt="Deepiri Logo" />

<br>

<a href="#overview">Overview</a> ·
<a href="#the-deepiri-philosophy">Philosophy</a> ·
<a href="#key-principles">Key Principles</a> ·
<a href="#tech-stack">Tech Stack</a> ·
<a href="#prerequisites">Prerequisites</a> ·
<a href="#getting-started">Getting Started</a> ·
<a href="#architecture">Architecture</a> ·
<a href="#engineering-standards">Engineering Standards</a> ·
<a href="#roadmap">Roadmap</a> ·
<a href="#collaboration--support">Collaboration & Support</a> ·
<a href="#team--mission">Team & Mission</a> ·
<a href="#license">License</a>

</div>

---

## Overview

Deepiri is a production-grade platform for building **scalable microservice systems** with **AI-powered workflows**. It abstracts infrastructure complexity *without hiding it*, allowing engineers to ship features quickly, maintain strict service boundaries, and scale confidently without rewrites.

The system is Kubernetes-native in design, while remaining developer-friendly in local environments.

## The Deepiri Philosophy

We believe that architecture is a living entity. Most platforms fail because they allow "architectural rot" — the slow creep of technical debt that makes systems impossible to maintain.

Deepiri is built to enforce:

- **Strict Logic Isolation** — no service leaks data into another
- **Environment Parity** — if it doesn't run in `run_dev.py`, it doesn't run in production
- **AI-Native Flow** — AI agents are system actors with their own ports and execution cycles, not chatbots bolted on afterward

## Key Principles

- **Clear domain boundaries** — every service owns its logic and data
- **Infrastructure realism** — local dev mimics production behavior
- **Minimal developer friction** — complexity lives in the platform, not the workflow
- **AI as a first-class system component**, not an afterthought

---

## Tech Stack

| Layer | Technologies |
|:------|:-------------|
| **Backend** | Node.js, Python (FastAPI / Flask), Go |
| **Frontend** | React.js, Vue.js, TypeScript |
| **Databases** | PostgreSQL, MongoDB, Redis, InfluxDB, Milvus |
| **Object Storage** | MinIO |
| **Coordination** | etcd |
| **AI / ML** | PyTorch, TensorFlow, NLP & ML APIs |
| **Cloud & DevOps** | Docker, Kubernetes, AWS, GCP, CI/CD pipelines |
| **Monitoring & Logging** | Prometheus, Grafana, ELK Stack |

---

## Prerequisites

Before running the stack, ensure the following are installed:

| Requirement | Minimum Version | Notes |
|:------------|:----------------|:------|
| **Python** | 3.10+ | Required for `run_dev.py` and Cyrex |
| **Node.js** | 18+ | Required for all TypeScript services |
| **Docker** | 24+ | Required for all containerized runtimes |
| **kubectl** | 1.27+ | Required for K8s secret management |

> **Windows users:** WSL2 is required. Native Windows is not supported.

---

## Getting Started

### Operations & Security

Unlike traditional setups that rely on scattered `.env` files, Deepiri mirrors **Kubernetes Secrets** locally. The `run_dev.py` script automates the entire local stack — it creates the Docker network, spins up all containers, injects ConfigMaps and Secrets natively, and waits for dependencies like PostgreSQL to be ready before proceeding.

```bash
python run_dev.py
```

**Supported on macOS, Linux, and Windows (WSL2).**

### Quick Validation

Once the stack is running, verify all containers are healthy:

```bash
docker ps
```

> All services should show a status of `Up`. If any container is restarting or exited, check its logs with `docker logs <container-name>`.

Key endpoints to confirm:

| Service | URL |
|:--------|:----|
| **Frontend** | http://localhost:5173 |
| **API Gateway** | http://localhost:5100 |
| **Cyrex API** | http://localhost:8000 |
| **MLflow** | http://localhost:5500 |
| **Jupyter** | http://localhost:8888 |
| **pgAdmin** | http://localhost:5050 |
| **MinIO Console** | http://localhost:9001 |

---

## Architecture

<p align="center">
  <img src="../assets/architecture.svg" alt="Deepiri Architecture" />
</p>

### Platform Services

| Service | Port | Description |
|:--------|:-----|:------------|
| **API Gateway** | `5100` | Entry point & request routing |
| **Auth Service** | `5001` | Authentication & authorization |
| **Task Orchestrator** | `5002` | Task coordination |
| **Engagement** | `5003` | Gamification |
| **Analytics** | `5004` | Platform analytics |
| **Notifications** | `5005` | Messaging & alerts |
| **External Bridge** | `5006` | Third-party integrations |
| **Realtime** | `5008` | WebSocket communication |

### AI / ML Services

| Service | Port | Description |
|:--------|:-----|:------------|
| **Cyrex API** | `8000` | AI agent execution |
| **Cyrex UI** | `5175` | Agent testing UI |
| **Jupyter** | `8888` | Research notebooks |
| **MLflow** | `5500` | Experiment tracking |

### Infrastructure

| Service | Port | Description |
|:--------|:-----|:------------|
| **pgAdmin** | `5050` | PostgreSQL management UI |
| **Adminer** | `8080` | Database management UI |
| **InfluxDB** | `8086` | Time-series data |
| **MinIO Console** | `9001` | Object storage UI |
| **Milvus** | `19530` | Vector database |

---

## Engineering Standards

We move fast without compromising system integrity. All contributions follow our SDLC:

- **Conventional Commits** — every commit must be prefixed (e.g., `feat:`, `fix:`, `docs:`) and follow our commit template for consistency
- **Domain-Specific Targeting** — contributors target the dev branch for their specific service
- **QA Verification** — all PRs are reviewed to ensure system integrity is maintained, features work as intended, and Docker containers are healthy

---

## Roadmap

| Phase | Focus | Status |
|:------|:------|:-------|
| **1** | Core API Gateway & Auth Service | ✅ |
| **2** | Cyrex AI Agent integration (Python Layer) | ✅ |
| **3** | Multi-cluster K8s deployment patterns | ●●● |
| **4** | Real-time event streaming via Redis Pub/Sub | ●●● |

---

## Collaboration & Support

We are a small, high-velocity team. To maintain our pace, we follow a spec-first collaboration model:

- **Issue Reporting** — before opening a PR, ensure there is an associated Issue with a defined Spec, Scope, and Success Criteria
- **Active Development** — we prioritize PRs that align with our philosophy and pass strict QA verification

## Team & Mission

Deepiri is powered by a **focused R&D collective** dedicated to building AI productivity tools. While the platform solves complex engineering challenges, our team drives the **vision, innovation, and community** behind it. Our mission includes designing, deploying, and maintaining scalable open-source AI tools that bridge research and real-world application.

### Connect With Us

| Resource | Contact |
|:---------|:--------|
| **Website** | [deepiri.com](https://deepiri.com) |
| **Discord** | [Deepiri Discord](https://discord.gg/B3Tx4Wmx) |
| **General Email** | [management@deepiri.com](mailto:management@deepiri.com) |
| **Support Inquiries** | [helpdesk@deepiri.com](mailto:helpdesk@deepiri.com) |

### Join the Team

We're always looking for contributors and collaborators. Send your resume or portfolio to [helpdesk@deepiri.com](mailto:helpdesk@deepiri.com) to be considered for our open-source R&D team.

---

## License

This project is licensed under the [Apache License 2.0](https://github.com/Team-Deepiri/deepiri-platform/blob/main/LICENSE.md). You are free to use, modify, and distribute this software, including for commercial purposes.

<br>

<div align="center">

**Code should scale as well as your ideas.**

*Deepiri makes that the default.*

</div>
