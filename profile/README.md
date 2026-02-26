<div align="center">

# DEEPIRI PLATFORM

<img src="logo.png" width="200" alt="Deepiri Logo">

**A high-performance, Kubernetes-oriented microservices platform with first-class AI agent integration.**

Designed to prevent **architectural rot** — the gradual loss of system quality as platforms scale.

[![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)](#)
[![Python](https://img.shields.io/badge/Python-14354C?style=for-the-badge&logo=python&logoColor=white)](#)
[![Kubernetes](https://img.shields.io/badge/kubernetes-%23326ce5.svg?style=for-the-badge&logo=kubernetes&logoColor=white)](#)
[![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)](#)
[![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB)](#)
[![PostgreSQL](https://img.shields.io/badge/postgresql-4169e1?style=for-the-badge&logo=postgresql&logoColor=white)](#)
[![Redis](https://img.shields.io/badge/redis-%23DD0031.svg?style=for-the-badge&logo=redis&logoColor=white)](#)

</div>

---

## Overview

Deepiri is a production-grade platform for building **scalable microservice systems** with **AI-powered workflows**.

It abstracts infrastructure complexity *without hiding it*, allowing engineers to:
- Ship features quickly
- Maintain strict service boundaries
- Scale confidently without rewrites

The system is Kubernetes-native in design, while remaining developer-friendly in local environments.

---

## Key Principles

- **Clear domain boundaries** — every service owns its logic and data
- **Infrastructure realism** — local dev mimics production behavior
- **Minimal developer friction** — complexity lives in the platform, not the workflow
- **AI as a first-class system component**, not an afterthought

---

## Getting Started

### Start the full stack

```bash
python run_dev.py

**Works on macOS, Windows (WSL), and Linux.**

> **Recommended:** `run_dev.py` loads Kubernetes-style configs from `ops/k8s/secrets`, eliminating the need for scattered `.env` files while preserving production parity.

---

## How It Works

### 1. API Gateway
All inbound traffic enters through the Gateway (Port 5000), which handles:
- Routing
- Rate limiting
- Authentication validation
- Redis-backed caching

### 2. Microservice Domains
Requests are forwarded to isolated TypeScript/Node.js services such as:
- Auth
- Task Orchestration
- Analytics
- Realtime communication

*Each service is independently deployable and scalable.*

### 3. AI & Automation Layer
AI workloads are delegated to Cyrex (Port 8000), a Python-based agent API:
- Task execution
- Experiment tracking via MLflow
- Research and prototyping via Jupyter

### 4. Persistence & Realtime State
- **PostgreSQL** for relational data
- **Redis** for caching, sessions, and realtime coordination

---

## Architecture Matrix

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

## License

This project is licensed under the Apache License 2.0.
You are free to use, modify, and distribute this software, including for commercial purposes, under the terms of the license.

<br>

<div align="center">

**Code should scale as well as your ideas.**

*Deepiri makes that the default.*

</div>