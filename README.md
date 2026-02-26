<div align="center">

# Deepiri

**A production-grade, Kubernetes-native platform for building scalable AI-powered microservices and AI-driven workflows.**

[![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)](#)
[![Python](https://img.shields.io/badge/Python-14354C?style=for-the-badge&logo=python&logoColor=white)](#)
[![Kubernetes](https://img.shields.io/badge/kubernetes-%23326ce5.svg?style=for-the-badge&logo=kubernetes&logoColor=white)](#)
[![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)](#)
[![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB)](#)
[![PostgreSQL](https://img.shields.io/badge/postgresql-4169e1?style=for-the-badge&logo=postgresql&logoColor=white)](#)
[![Redis](https://img.shields.io/badge/redis-%23DD0031.svg?style=for-the-badge&logo=redis&logoColor=white)](#)

</div>

<br>

<p align="center">
  <img src="assets/deepiri-logo.png" alt="Deepiri Logo" />
</p>

<br>

Overview · The Deepiri Philosophy · Key Principles · Prerequisites · Getting Started · How It Works · Roadmap · Engineering Standards · Collaboration & Support · Team & Mission · License

## Overview

Deepiri is a production-grade platform for building **scalable microservice systems** with **AI-powered workflows**. It abstracts infrastructure complexity *without hiding it*, allowing engineers to ship features quickly, maintain strict service boundaries, and scale confidently without rewrites.

The system is Kubernetes-native in design, while remaining developer-friendly in local environments.

---

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

## Prerequisites

Before running the stack, ensure the following are installed:

| Requirement | Minimum Version | Notes |
|-------------|-----------------|-------|
| **Python** | 3.10+ | Required for `run_dev.py` and Cyrex |
| **Node.js** | 18+ | Required for all TypeScript services |
| **Docker** | 24+ | Required for containerized runtimes |
| **kubectl** | 1.27+ | Required for K8s secret management |

> **Windows users:** WSL2 is required. Native Windows is not supported.

---

## Getting Started

### Operations & Security

Unlike traditional setups that rely on scattered `.env` files, Deepiri mirrors **Kubernetes Secrets** locally.

- **Secret Injection** — `run_dev.py` dynamically injects configurations from `ops/k8s/secrets` into the service environment
- **Isolated Runtimes** — every service runs in its own process space with a dedicated port, preventing port-shadowing and resource contention

### Start the full stack

```bash
python run_dev.py
```

**Supported on macOS, Linux, and Windows (WSL2).**

---

## How It Works

### 1. API Gateway
All inbound traffic enters through the Gateway on port `5000`, which handles routing, rate limiting, authentication validation, and Redis-backed caching.

### 2. Microservice Domains
Requests are forwarded to isolated TypeScript/Node.js services — Auth, Task Orchestration, Analytics, Realtime, and others. Each service is independently deployable and scalable.

### 3. AI & Automation Layer — Cyrex
AI workloads are handled by **Cyrex** (`8000`), a dedicated Python-based agent runtime. Cyrex manages task execution, experiment tracking via MLflow, and research environments via Jupyter. It runs as a fully separate service because AI workloads have distinct runtime characteristics — longer execution cycles, heavier compute, and different failure modes than standard microservices.

### 4. Persistence & Realtime State
- **PostgreSQL** for relational data
- **Redis** for caching, sessions, and realtime coordination

---

## Architecture

### Platform Services

| Service | Port | Description |
|---------|------|-------------|
| **API Gateway** | `5000` | Entry point & request routing |
| **Auth Service** | `5001` | Authentication & authorization |
| **Task Orchestrator** | `5002` | Task coordination |
| **Engagement** | `5003` | Gamification |
| **Analytics** | `5004` | Platform analytics |
| **Notifications** | `5005` | Messaging & alerts |
| **External Bridge** | `5006` | Third-party integrations |
| **Realtime** | `5008` | WebSocket communication |

### AI / ML Services

| Service | Port | Description |
|---------|------|-------------|
| **Cyrex API** | `8000` | AI agent execution |
| **Cyrex UI** | `5175` | Agent testing UI |
| **Jupyter** | `8888` | Research notebooks |
| **MLflow** | `5500` | Experiment tracking |

---

## Engineering Standards

We move fast without compromising system integrity. All contributions follow our SDLC:

- **Conventional Commits** — every commit must be prefixed (e.g., `feat:`, `fix:`, `docs:`) and follow a template to maintian consistency and clarity
- **Domain-Specific Targeting** — contributors target the dev branch for their specific service
- **QA Verification** — all PRs are reviewed to ensure system integrity is maintained, features work as intened, and docker containers are healthy

---

## Roadmap

| Phase | Focus | Status |
|-------|-------|--------|
| **1** | Core API Gateway & Auth Service | ✅ Complete |
| **2** | Cyrex AI Agent integration (Python Layer) | ✅ Complete |
| **3** | Multi-cluster K8s deployment patterns | 🔄 In Progress |
| **4** | Real-time event streaming via Redis Pub/Sub |   Planned |

---

## Collaboration & Support

We are a small, high-velocity team. To maintain our pace, we follow a spec-first collaboration model:

- **Issue Reporting** — before opening a PR, ensure there is an associated Issue with a defined Spec, Scope, and Success Criteria
- **Active Development** — we prioritize PRs that align with our philosophy and pass strict QA verification

---

## Team & Mission

Deepiri is powered by a **focused R&D collective** dedicated to building AI productivity tools. While the platform solves complex engineering challenges, our team drives the **vision, innovation, and community** behind it. Our mission also includes designing, deploying, and maintaining scalable open source AI tools that bridge research and real-world application.

### Connect With Us

| Resource | Contact |
| :--- | :--- |
| **Website** | [deepiri.com](https://deepiri.com) |
| **Discord** | [Deepiri Discord](https://discord.gg/B3Tx4Wmx) |
| **General Email** | [management@deepiri.com](mailto:management@deepiri.com) |
| **Support Inquiries** | [helpdesk@deepiri.com](mailto:helpdesk@deepiri.com) |

### Join the Team

We're always looking for contributors and collaborators. Send your resume or portfolio to [helpdesk@deepiri.com](mailto:helpdesk@deepiri.com) to be considered for our open-source R&D team.

---

## License

This project is licensed under the [Apache License 2.0](./LICENSE.md). You are free to use, modify, and distribute this software, including for commercial purposes.

<br>

<div align="center">

**Code should scale as well as your ideas.**

*Deepiri makes that the default.*

</div>