---
layout: home
title: Home
nav_order: 1
description: "Accelerate software development with AI-powered specification and implementation using GitHub Copilot Spec-kit"
permalink: /
---

# Overview GitHub Spec-kit — Workshop
{: .fs-9 }

Accelerate software development with **AI-powered specification and implementation** using GitHub Copilot Spec-kit — a structured workflow that transforms natural language feature descriptions into production-ready code.
{: .fs-6 .fw-300 }

[Get Started](/Overview-Github-Spec-kit/modules/01-prerequisites/){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[View Workflow](/Overview-Github-Spec-kit/modules/02-speckit-overview/){: .btn .fs-5 .mb-4 .mb-md-0 }

---

## What is Spec-kit?

Spec-kit is a **structured AI-powered development workflow** that integrates directly into VS Code through GitHub Copilot Agent Mode. It provides a repeatable, governance-aware pipeline that transforms a simple natural language feature description into a fully implemented, production-ready codebase — complete with backend services, frontend interfaces, infrastructure scripts, and automated tests.

Unlike ad-hoc prompting or unstructured code generation, Spec-kit enforces a disciplined progression through discrete stages: specification, clarification, planning, task decomposition, implementation, and analysis. Each stage produces traceable artifacts that serve as inputs for the next, ensuring architectural consistency, requirement coverage, and cross-artifact integrity throughout the entire software development lifecycle.

## Spec-kit Workflow

The following diagram illustrates the end-to-end Spec-kit pipeline — from a natural language feature idea through to validated production code:

```mermaid
%%{init: {'theme': 'default', 'themeVariables': {'fontSize': '12px'}}}%%
flowchart LR
    A[Feature Idea] --> B["/speckit.specify"]
    B --> C["/speckit.clarify"]
    C --> D["/speckit.plan"]
    D --> E["/speckit.tasks"]
    E --> F["/speckit.implement"]
    F --> G["/speckit.analyze"]

    B -->|spec.md| C
    C -->|Refined spec.md| D
    D -->|plan.md\ndata-model.md\ncontracts/| E
    E -->|tasks.md| F
    F -->|Source Code| G
    G -->|Validation Report| H[Done ✓]

    style A fill:#4CAF50,color:#fff
    style H fill:#2196F3,color:#fff
```

| Stage | Command | Output Artifact |
|---|---|---|
| Specify | `/speckit.specify` | Feature specification (`spec.md`) |
| Clarify | `/speckit.clarify` | Refined spec with resolved ambiguities |
| Plan | `/speckit.plan` | Architecture, data model, API contracts |
| Tasks | `/speckit.tasks` | Dependency-ordered task list (`tasks.md`) |
| Implement | `/speckit.implement` | Production code for all tasks |
| Analyze | `/speckit.analyze` | Cross-artifact consistency report |

---

## Example Business Case

This workshop demonstrates the Spec-kit workflow by building a complete **Azure Cost Monitoring Tool** — an internal dashboard that ingests daily cost data from the Azure Consumption API into PostgreSQL, serves aggregated views via a FastAPI backend, and displays interactive charts through a React frontend.

### Architecture at a Glance

| Component | Technology | Azure Resource |
|---|---|---|
| 🖥️ Frontend | React + Vite + TypeScript | Static Web Apps |
| ⚙️ Backend | Python + FastAPI | App Service Linux |
| 🗄️ Database | PostgreSQL 16 | Flexible Server (VNet) |
| ⏱️ Scheduler | Azure Functions (Timer) | Consumption Plan |
| 🔐 Secrets | Key Vault | Standard |
| 🌐 Networking | Hub-Spoke VNet | Azure Firewall |
| 📊 Monitoring | Application Insights | Log Analytics |

### What Gets Generated

Using the Spec-kit pipeline, a single natural language description produces:

- **88 implementation tasks** across 8 phases
- **60+ source files** (~8,000 lines of code)
- **Backend**: FastAPI with SQLAlchemy ORM, Alembic migrations, JWT auth
- **Frontend**: React pages with TanStack Query, Recharts, responsive layout
- **Infrastructure**: Azure CLI provisioning scripts (hub-spoke networking)
- **Tests**: Unit tests (pytest, Vitest) and integration test scaffolding
- **DevOps**: Dockerfile, docker-compose, CI/CD workflow

---

## Workshop Modules

| # | Module | Duration | Description |
|---|---|---|---|
| 1 | [Prerequisites](/Overview-Github-Spec-kit/modules/01-prerequisites/) | 10 min | Set up your environment |
| 2 | [Spec-kit Overview](/Overview-Github-Spec-kit/modules/02-speckit-overview/) | 15 min | Understand the workflow |
| 3 | [Specification](/Overview-Github-Spec-kit/modules/03-specification/) | 20 min | Create a feature spec |
| 4 | [Planning](/Overview-Github-Spec-kit/modules/04-planning/) | 20 min | Generate the implementation plan |
| 5 | [Task Generation](/Overview-Github-Spec-kit/modules/05-task-generation/) | 15 min | Produce executable task list |
| 6 | [Implementation](/Overview-Github-Spec-kit/modules/06-implementation/) | 30 min | Execute all tasks with AI |
| 7 | [Analysis & Review](/Overview-Github-Spec-kit/modules/07-analysis-review/) | 10 min | Validate and iterate |

**Total estimated time: ~2 hours**
{: .fs-5 .fw-300 }

## Key Design Decisions

- **Structured over ad-hoc** — Spec-kit enforces a repeatable specification → plan → tasks → implement pipeline
- **GitHub Copilot Agent Mode** — Leverages VS Code agent capabilities for multi-file code generation
- **Artifact traceability** — Every implementation decision traces back to spec requirements
- **Constitution governance** — Project-wide principles enforced across all generated artifacts
- **PaaS-first architecture** — Demo project uses Azure managed services exclusively (no VMs/AKS)

---

{: .note }
> This workshop uses the **Azure Cost Monitoring Tool** as a demonstration project. The Spec-kit workflow itself is technology-agnostic and can be applied to any software project.
