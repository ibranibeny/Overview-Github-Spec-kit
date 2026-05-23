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

## The Spec-kit Pipeline

```mermaid
%%{init: {'theme': 'default', 'themeVariables': {'fontSize': '14px'}}}%%
flowchart TD
    A["Feature Idea"] --> B["/speckit.constitution"]
    B --> C["/speckit.specify"]
    C --> D["/speckit.clarify"]
    D --> E["/speckit.plan"]
    E --> F["/speckit.tasks"]
    F --> G["/speckit.implement"]
    G --> H["/speckit.analyze"]
    H --> I["Done ✓"]

    B -.- B1["constitution.md"]
    C -.- C1["spec.md"]
    D -.- D1["Refined spec.md"]
    E -.- E1["plan.md + data-model.md + contracts/"]
    F -.- F1["tasks.md"]
    G -.- G1["Source code (all files)"]
    H -.- H1["Validation report"]

    classDef artifact fill:#E3F2FD,stroke:#1565C0,color:#1565C0
    class B1,C1,D1,E1,F1,G1,H1 artifact

    style A fill:#FF9800,color:#fff
    style I fill:#4CAF50,color:#fff
```

## What You'll Build

A complete **Azure Cost Monitoring Tool** using the Spec-kit workflow, demonstrating:

- **Project Constitution** — Define governance principles that enforce consistency across all artifacts
- **Feature Specification** — Transform a natural language description into a structured spec
- **Automated Planning** — Generate architecture, data models, API contracts, and implementation plans
- **Task Decomposition** — Break down complex features into dependency-ordered, executable tasks
- **AI-Powered Implementation** — Execute all 88 tasks automatically with GitHub Copilot
- **Quality Analysis** — Validate consistency across all generated artifacts

## Architecture at a Glance

| Component | Technology | Azure Resource |
|---|---|---|
| 🖥️ Frontend | React + Vite + TypeScript | Static Web Apps |
| ⚙️ Backend | Python + FastAPI | App Service Linux |
| 🗄️ Database | PostgreSQL 16 | Flexible Server (VNet) |
| ⏱️ Scheduler | Azure Functions (Timer) | Consumption Plan |
| 🔐 Secrets | Key Vault | Standard |
| 🌐 Networking | Hub-Spoke VNet | Azure Firewall |
| 📊 Monitoring | Application Insights | Log Analytics |

## Workshop Modules

| # | Module | Duration | Description |
|---|---|---|---|
| 1 | [Prerequisites](/Overview-Github-Spec-kit/modules/01-prerequisites/) | 10 min | Set up your environment |
| 2 | [Spec-kit Overview](/Overview-Github-Spec-kit/modules/02-speckit-overview/) | 15 min | Understand the workflow |
| 3 | [Constitution](/Overview-Github-Spec-kit/modules/03-constitution/) | 10 min | Define project governance |
| 4 | [Specification](/Overview-Github-Spec-kit/modules/04-specification/) | 20 min | Create a feature spec |
| 5 | [Planning](/Overview-Github-Spec-kit/modules/05-planning/) | 20 min | Generate the implementation plan |
| 6 | [Task Generation](/Overview-Github-Spec-kit/modules/06-task-generation/) | 15 min | Produce executable task list |
| 7 | [Implementation](/Overview-Github-Spec-kit/modules/07-implementation/) | 30 min | Execute all tasks with AI |
| 8 | [Analysis & Review](/Overview-Github-Spec-kit/modules/08-analysis-review/) | 10 min | Validate and iterate |

**Total estimated time: ~2.5 hours**
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
