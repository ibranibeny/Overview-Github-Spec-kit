---
layout: default
title: "Step 1: Specify"
parent: Demo Walkthrough
nav_order: 1
permalink: /demo/step-1-specify/
---

# Step 1 — Define the Feature & Specify
{: .no_toc }

Transform a natural language description into a structured feature specification.
{: .fs-6 .fw-300 }

<details open markdown="block">
  <summary>Table of Contents</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## 1.1 The Input

Open VS Code Copilot Chat and type the following command with your feature description:

```text
/speckit.specify Build an Azure Cost Monitoring Tool to monitor Azure costs 
end-to-end: ingest daily cost data from Azure Consumption API into PostgreSQL, 
serve aggregated views via FastAPI backend, and display interactive charts 
through a React frontend.
```

{: .note }
> The description should be concise (1–3 sentences) but capture the core functionality, data flow, and technology preferences.

## 1.2 What Spec-kit Generates

The command produces `specs/001-azure-cost-monitoring/spec.md` with a complete, structured specification:

### Generated Specification Structure

```markdown
# Feature Specification: Azure Cost Monitoring Tool

**Feature Branch**: 001-azure-cost-monitoring
**Created**: 2026-05-23
**Status**: Draft
```

## 1.3 User Stories (Auto-Generated)

Spec-kit automatically decomposes your description into prioritized user stories:

| # | User Story | Priority | Description |
|---|---|---|---|
| US1 | View Daily Cost Dashboard | P1 | Daily/MTD costs, top contributors, trend chart, anomalies |
| US2 | Data Ingestion & Refresh | P1 | Daily automated + manual ingestion from Azure Consumption API |
| US3 | Authentication & User Management | P1 | Login, JWT auth, role-based access, admin CRUD |
| US4 | Detailed Cost Exploration & Export | P2 | Filterable detail table with pagination + CSV export |
| US5 | Budgets & Alerts | P2 | Budget creation per scope with threshold alerts |
| US6 | Audit Logging | P2 | Track all admin actions with timestamps |

## 1.4 Acceptance Criteria (Example)

Each user story includes testable acceptance scenarios:

```markdown
### User Story 1 - View Daily Cost Dashboard (Priority: P1)

As an engineer/FinOps viewer, I want to see a dashboard showing daily and 
month-to-date costs, top cost contributors, cost by tag, and anomaly 
highlights so that I can quickly understand my Azure spending.

**Acceptance Scenarios**:

1. Given a Viewer is authenticated and cost data exists, 
   When they open the dashboard, 
   Then they see total cost (daily and MTD), a trend chart, 
   top N cost contributors, and anomalies highlighted.

2. Given cost data exists for the last 30 days, 
   When the dashboard loads, 
   Then anomaly detection highlights any day where cost deviates 
   significantly (>2σ) from the 7-day rolling baseline.

3. Given the dashboard is displayed, 
   When the user changes the scope filter, 
   Then all widgets update within 2 seconds.
```

## 1.5 Output File Location

After running `/speckit.specify`, your workspace contains:

```text
specs/001-azure-cost-monitoring/
└── spec.md              ← Feature specification (auto-generated)
```

## 1.6 Key Observations

| Aspect | Result |
|---|---|
| User Stories Generated | 6 (prioritized P1/P2) |
| Acceptance Scenarios | 20+ testable conditions |
| Non-Goals Identified | Multi-cloud, real-time streaming, invoice generation |
| Performance Targets | Dashboard <2s, API p95 <500ms, CSV export <10s |
| Security Model | JWT with bcrypt, role-based (Admin/Viewer) |

{: .important }
> Notice how a 2-sentence description expanded into 6 user stories with 20+ acceptance criteria. Spec-kit fills in the gaps based on best practices and the project constitution.

---

[← Demo Overview](/Overview-Github-Spec-kit/demo/) | [Next: Clarify Requirements →](/Overview-Github-Spec-kit/demo/step-2-clarify/)
