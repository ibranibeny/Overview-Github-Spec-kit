---
layout: default
title: 5. Planning
nav_order: 6
permalink: /modules/05-planning/
---

# Module 5 — Planning
{: .no_toc }

Generate the implementation plan including architecture decisions, data models, API contracts, and project structure using `/speckit.plan`.
{: .fs-6 .fw-300 }

<details open markdown="block">
  <summary>Table of Contents</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## 4.1 The Plan Command

The `/speckit.plan` command reads your `spec.md` and constitution, then generates a comprehensive implementation plan with multiple artifacts:

```
/speckit.plan
```

{: .note }
> The plan command may take 2–3 minutes to complete as it generates multiple interrelated documents.

## 4.2 Generated Artifacts

| Artifact | File | Purpose |
|---|---|---|
| Implementation Plan | `plan.md` | Tech stack, architecture, project structure |
| Research | `research.md` | Technology decisions with rationale |
| Data Model | `data-model.md` | Database schema, entities, relationships |
| API Contract | `contracts/openapi.yaml` | REST API specification |
| Quickstart | `quickstart.md` | Local development setup guide |

## 4.3 Plan Structure

The `plan.md` file includes:

### Summary Section

```markdown
# Implementation Plan: Azure Cost Monitoring Tool

**Branch**: `001-azure-cost-monitoring`
**Date**: 2026-05-23
**Spec**: `specs/001-azure-cost-monitoring/spec.md`

## Summary
Build an internal Azure cost monitoring dashboard that ingests daily 
cost data from the Azure Consumption API into PostgreSQL...
```

### Technical Context

```markdown
## Technical Context

**Language/Version**: Python 3.11 (backend), TypeScript 5.x (frontend)
**Primary Dependencies**: FastAPI, SQLAlchemy, React 18, Vite 5, Recharts
**Storage**: Azure Database for PostgreSQL Flexible Server (v16)
**Testing**: pytest + httpx (backend), Vitest + Testing Library (frontend)
**Target Platform**: Azure PaaS — App Service, Static Web Apps, Functions
```

### Constitution Check

The plan validates all constitution principles:

| # | Principle | Status | Evidence |
|---|---|---|---|
| 1 | PaaS-First | ✅ PASS | App Service + Static Web Apps + Functions |
| 2 | Hub-Spoke Networking | ✅ PASS | Hub VNet + Spoke-APP + Spoke-DATA |
| 3 | Azure CLI IaC | ✅ PASS | Scripts in `/infra` directory |
| 4 | Auth Model | ✅ PASS | JWT with bcrypt, pluggable AuthProvider |
| 5 | App Stack | ✅ PASS | FastAPI backend, React + Vite frontend |

{: .important }
> If any constitution principle fails, the plan command halts and requires you to either adjust the spec or add an explicit justification.

### Project Structure

The plan defines the complete file layout for the implementation:

```text
backend/
├── app/
│   ├── main.py
│   ├── config.py
│   ├── models/
│   ├── schemas/
│   ├── api/
│   ├── services/
│   └── middleware/
├── alembic/
├── tests/
├── requirements.txt
└── Dockerfile

frontend/
├── src/
│   ├── components/
│   ├── pages/
│   ├── services/
│   ├── hooks/
│   └── App.tsx
├── tests/
├── vite.config.ts
└── package.json

infra/
├── 00-variables.sh
├── 01-networking.sh
├── 02-data-tier.sh
├── 03-app-tier.sh
├── 04-functions.sh
└── 05-ops-monitoring.sh
```

## 4.4 Data Model

The `data-model.md` artifact defines database entities:

```markdown
## Entities

### cost_records
| Column | Type | Constraints |
|---|---|---|
| id | UUID | PK, default gen_random_uuid() |
| date | DATE | NOT NULL, indexed |
| resource_group | VARCHAR(90) | NOT NULL |
| service_name | VARCHAR(256) | NOT NULL |
| cost_amount | NUMERIC(12,4) | NOT NULL |
| currency | VARCHAR(3) | DEFAULT 'USD' |

### budgets
| Column | Type | Constraints |
|---|---|---|
| id | UUID | PK |
| name | VARCHAR(100) | NOT NULL, UNIQUE |
| amount | NUMERIC(12,2) | NOT NULL |
| period | VARCHAR(20) | 'monthly' or 'quarterly' |
| threshold_percent | INTEGER | DEFAULT 80 |
```

## 4.5 API Contract

The `contracts/openapi.yaml` defines all REST endpoints:

```yaml
paths:
  /api/v1/costs/summary:
    get:
      summary: Get cost summary for dashboard
      parameters:
        - name: start_date
          in: query
          schema:
            type: string
            format: date
        - name: group_by
          in: query
          schema:
            type: string
            enum: [resource_group, service, tag]
```

## 4.6 Hands-On Exercise

1. Ensure `spec.md` exists from Module 3
2. Run the plan command:
   ```
   /speckit.plan
   ```
3. Review each generated artifact:
   - `plan.md` — Verify tech stack and structure
   - `data-model.md` — Validate entity relationships
   - `contracts/openapi.yaml` — Check endpoint definitions
   - `research.md` — Review technology decisions
4. Verify the constitution check passes

## Checklist

Before proceeding to Module 5:

- ☐ `/speckit.plan` executed successfully
- ☐ `plan.md` generated with complete project structure
- ☐ `data-model.md` defines all entities and relationships
- ☐ `contracts/openapi.yaml` specifies all API endpoints
- ☐ Constitution check passes (all principles ✅)
- ☐ `research.md` documents technology decisions

---

[← Specification](/Overview-Github-Spec-kit/modules/04-specification/) | [Next: Task Generation →](/Overview-Github-Spec-kit/modules/06-task-generation/)
