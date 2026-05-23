---
layout: default
title: 4. Specification
nav_order: 5
permalink: /modules/04-specification/
---

# Module 4 — Specification
{: .no_toc }

Create a feature specification from a natural language description using `/speckit.specify` and refine it with `/speckit.clarify`.
{: .fs-6 .fw-300 }

<details open markdown="block">
  <summary>Table of Contents</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## 3.1 The Specification Command

The `/speckit.specify` command transforms a natural language feature description into a structured specification document (`spec.md`).

### Invocation

In the VS Code Copilot Chat panel, type:

```
/speckit.specify Build an internal Azure cost monitoring dashboard that ingests 
daily cost data from the Azure Consumption API into PostgreSQL, serves aggregated 
views via a FastAPI backend, and displays interactive charts through a React frontend.
```

{: .note }
> The feature description should be concise but complete. Include the core functionality, key constraints, and target platform. One to three sentences is typical.

## 3.2 Specification Output

The command generates a `spec.md` file with the following sections:

| Section | Content |
|---|---|
| **Title & Summary** | Feature name and one-line description |
| **Goals** | What the feature achieves (user-facing outcomes) |
| **Non-Goals** | Explicitly excluded scope |
| **Functional Requirements** | Detailed behavior descriptions |
| **Non-Functional Requirements** | Performance, security, scalability targets |
| **Constraints** | Technology, compliance, or business limitations |
| **Acceptance Criteria** | Testable conditions for completion |

### Example Output Structure

```markdown
# Feature: Azure Cost Monitoring Tool

## Summary
Internal dashboard for tracking Azure subscription costs...

## Goals
- Daily automated cost ingestion from Azure Consumption API
- Interactive dashboard with drill-down by resource group, service, tag
- Budget alerts with threshold notifications
...

## Non-Goals
- Multi-cloud support (AWS/GCP)
- Real-time streaming cost data
- Billing invoice generation
...
```

## 3.3 Refining with Clarify

After initial specification, run `/speckit.clarify` to identify underspecified areas:

```
/speckit.clarify
```

The command asks up to **5 targeted clarification questions**, such as:

1. "Should the authentication use Azure AD SSO or a local credential store?"
2. "What is the expected data retention period for historical cost records?"
3. "Should budget alerts trigger email notifications or in-app only?"

{: .tip }
> Answer each question directly. The clarify command encodes your answers back into the spec, producing a more precise specification.

## 3.4 Constitution Setup

Before running `/speckit.specify`, you may optionally set up a project constitution:

```
/speckit.constitution
```

This creates `.specify/memory/constitution.md` with your project-wide principles. For the workshop demonstration, the constitution includes:

```markdown
## Principles

1. **PaaS-First** — All infrastructure must use Azure PaaS services (no VMs, no AKS)
2. **Hub-Spoke Networking** — VNets follow hub-spoke topology with Azure Firewall
3. **Azure CLI IaC** — All infrastructure provisioned via `az` commands only
4. **Auth Model** — Static login with JWT (access + refresh tokens)
5. **App Stack** — Python + FastAPI backend, TypeScript + React + Vite frontend
6. **Observability** — Application Insights with structured logging
```

## 3.5 Hands-On Exercise

1. Open VS Code with an empty workspace
2. Open Copilot Chat (`Ctrl+Shift+I`)
3. Run the constitution command:
   ```
   /speckit.constitution
   ```
4. Define at least 3 architectural principles
5. Run the specify command with your feature description:
   ```
   /speckit.specify <your feature description>
   ```
6. Review the generated `spec.md`
7. Run clarify to refine:
   ```
   /speckit.clarify
   ```
8. Answer the clarification questions

## 3.6 Expected Results

After completing this module, your workspace should contain:

```text
.specify/
└── memory/
    └── constitution.md

specs/001-your-feature/
└── spec.md
```

## Checklist

Before proceeding to Module 4:

- ☐ Constitution created with project principles
- ☐ `/speckit.specify` executed successfully
- ☐ `spec.md` generated with all sections populated
- ☐ `/speckit.clarify` executed and questions answered
- ☐ Spec refined with clarification answers

---

[← Constitution](/Overview-Github-Spec-kit/modules/03-constitution/) | [Next: Planning →](/Overview-Github-Spec-kit/modules/05-planning/)
