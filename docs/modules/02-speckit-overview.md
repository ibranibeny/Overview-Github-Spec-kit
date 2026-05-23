---
layout: default
title: 2. Spec-kit Overview
nav_order: 3
permalink: /modules/02-speckit-overview/
---

# Module 2 — Spec-kit Overview
{: .no_toc }

Understand the Spec-kit workflow, its components, and how it transforms natural language descriptions into production-ready code.
{: .fs-6 .fw-300 }

<details open markdown="block">
  <summary>Table of Contents</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## 2.1 What is Spec-kit?

Spec-kit is a **structured AI-powered workflow** for GitHub Copilot that bridges the gap between a feature idea and its complete implementation. It provides a repeatable pipeline of commands that generate progressively more detailed artifacts — from high-level specification through to executable code.

| Stage | Command | Output |
|---|---|---|
| Specify | `/speckit.specify` | Feature specification (`spec.md`) |
| Clarify | `/speckit.clarify` | Refined spec with answered questions |
| Plan | `/speckit.plan` | Architecture, data model, API contracts |
| Tasks | `/speckit.tasks` | Dependency-ordered task list (`tasks.md`) |
| Implement | `/speckit.implement` | Production code for all tasks |
| Analyze | `/speckit.analyze` | Consistency validation report |

## 2.2 Workflow Pipeline

The Spec-kit workflow follows a linear progression with feedback loops:

```mermaid
%%{init: {'theme': 'default', 'themeVariables': {'fontSize': '12px'}}}%%
flowchart TD
    A["Feature Idea"] --> B["/speckit.specify"]
    B -->|"spec.md"| C["/speckit.clarify"]
    C -->|"Refined spec.md"| D["/speckit.plan"]
    D -->|"plan.md + data-model.md + contracts/"| E["/speckit.tasks"]
    E -->|"tasks.md (dependency-ordered)"| F["/speckit.implement"]
    F -->|"Source code (all files)"| G["/speckit.analyze"]
    G -->|"Validation report"| H["Done ✓"]

    style A fill:#FF9800,color:#fff
    style H fill:#4CAF50,color:#fff
```

## 2.3 Artifact Structure

All Spec-kit artifacts are stored in a `specs/` directory within your project:

```text
specs/001-feature-name/
├── spec.md              # Feature specification
├── plan.md              # Implementation plan
├── research.md          # Technology decisions
├── data-model.md        # Database schema
├── quickstart.md        # Setup guide
├── contracts/
│   └── openapi.yaml     # API contract
├── tasks.md             # Executable task list
└── checklists/          # Quality checklists (optional)
    ├── ux.md
    ├── test.md
    └── security.md
```

## 2.4 Constitution

The **constitution** is a project-wide governance document (`.specify/memory/constitution.md`) that defines architectural principles enforced across all Spec-kit commands. Examples include:

- Technology stack requirements (e.g., "PaaS-first, no VMs")
- Authentication model (e.g., "JWT with refresh tokens")
- Infrastructure approach (e.g., "Azure CLI only, no Bicep/Terraform")
- Networking topology (e.g., "Hub-spoke VNet architecture")

{: .important }
> The constitution is checked at the start of every Spec-kit command. Violations halt execution and require explicit justification.

## 2.5 Git Integration

Spec-kit includes optional Git workflow commands:

| Command | Purpose |
|---|---|
| `/speckit.git.initialize` | Initialize a Git repository |
| `/speckit.git.feature` | Create a numbered feature branch |
| `/speckit.git.commit` | Auto-commit after each Spec-kit step |
| `/speckit.git.validate` | Validate branch naming conventions |

## 2.6 Key Benefits

| Benefit | Description |
|---|---|
| **Repeatability** | Same workflow produces consistent, high-quality output |
| **Traceability** | Every line of code traces back to a specification requirement |
| **Governance** | Constitution enforces project-wide architectural decisions |
| **Speed** | 88 implementation tasks executed in a single session |
| **Quality** | Cross-artifact consistency validated automatically |
| **Documentation** | Spec, plan, and contracts generated as byproducts |

## Checklist

Before proceeding to Module 3:

- ☐ Understand the 6-stage Spec-kit pipeline
- ☐ Know the artifact structure (`specs/` directory)
- ☐ Understand the role of the constitution
- ☐ Familiar with Git integration commands

---

[← Prerequisites](/Overview-Github-Spec-kit/modules/01-prerequisites/) | [Next: Specification →](/Overview-Github-Spec-kit/modules/03-specification/)
