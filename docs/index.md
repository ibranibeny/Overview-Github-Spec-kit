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

[Get Started]({{ site.baseurl }}{% link modules/01-prerequisites.md %}){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[View Workflow]({{ site.baseurl }}{% link modules/02-speckit-overview.md %}){: .btn .fs-5 .mb-4 .mb-md-0 }

---

## What You'll Build

A complete **Azure Cost Monitoring Tool** using the Spec-kit workflow, demonstrating:

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
| 1 | [Prerequisites]({{ site.baseurl }}{% link modules/01-prerequisites.md %}) | 10 min | Set up your environment |
| 2 | [Spec-kit Overview]({{ site.baseurl }}{% link modules/02-speckit-overview.md %}) | 15 min | Understand the workflow |
| 3 | [Specification]({{ site.baseurl }}{% link modules/03-specification.md %}) | 20 min | Create a feature spec |
| 4 | [Planning]({{ site.baseurl }}{% link modules/04-planning.md %}) | 20 min | Generate the implementation plan |
| 5 | [Task Generation]({{ site.baseurl }}{% link modules/05-task-generation.md %}) | 15 min | Produce executable task list |
| 6 | [Implementation]({{ site.baseurl }}{% link modules/06-implementation.md %}) | 30 min | Execute all tasks with AI |
| 7 | [Analysis & Review]({{ site.baseurl }}{% link modules/07-analysis-review.md %}) | 10 min | Validate and iterate |

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
