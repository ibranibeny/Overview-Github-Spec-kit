---
layout: default
title: 7. Implementation
nav_order: 8
permalink: /modules/07-implementation/
---

# Module 7 — Implementation
{: .no_toc }

Execute all tasks automatically using `/speckit.implement` — the AI-powered code generation engine that produces production-ready code from your task list.
{: .fs-6 .fw-300 }

<details open markdown="block">
  <summary>Table of Contents</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## 6.1 The Implement Command

The `/speckit.implement` command reads `tasks.md` and executes every task sequentially, generating all source code:

```
/speckit.implement
```

{: .important }
> This command may take **15–45 minutes** depending on project complexity and task count. For the demonstration project (88 tasks), expect approximately 30 minutes of execution.

## 6.2 Execution Flow

The implement command follows a strict execution protocol:

1. **Pre-flight checks** — Validates `tasks.md`, `plan.md`, and constitution exist
2. **Checklist validation** — If checklists exist, verifies completion status
3. **Context loading** — Reads all artifacts (plan, data model, contracts, research)
4. **Project setup** — Creates ignore files (`.gitignore`, `.dockerignore`, etc.)
5. **Phase execution** — Processes tasks phase-by-phase in dependency order
6. **Progress tracking** — Marks completed tasks with `[X]` in `tasks.md`
7. **Completion validation** — Verifies all tasks marked complete

## 6.3 What Gets Generated

For the Azure Cost Monitoring Tool, implementation produces:

### Backend (Python + FastAPI)

| Component | Files | Purpose |
|---|---|---|
| App Factory | `main.py`, `config.py` | Application entry point |
| Models | `models/*.py` | SQLAlchemy ORM entities |
| Schemas | `schemas/*.py` | Pydantic request/response |
| API Routes | `api/*.py` | REST endpoint handlers |
| Services | `services/*.py` | Business logic layer |
| Middleware | `middleware/*.py` | CORS, correlation ID, errors |
| Migrations | `alembic/` | Database schema management |
| Tests | `tests/` | Unit and integration tests |

### Frontend (React + Vite + TypeScript)

| Component | Files | Purpose |
|---|---|---|
| Pages | `pages/*.tsx` | Dashboard, Details, Budgets, Login |
| Components | `components/*.tsx` | Charts, tables, navigation |
| Hooks | `hooks/*.ts` | TanStack Query data fetching |
| Services | `services/api.ts` | HTTP client configuration |
| Store | `store/*.ts` | Authentication state |

### Infrastructure (Azure CLI)

| Script | Purpose |
|---|---|
| `00-variables.sh` | Shared naming conventions and CIDRs |
| `01-networking.sh` | Hub-spoke VNets, firewall, route tables |
| `02-data-tier.sh` | PostgreSQL Flexible Server |
| `03-app-tier.sh` | App Service + Static Web Apps |
| `04-functions.sh` | Azure Functions (timer trigger) |
| `05-ops-monitoring.sh` | Application Insights + alerts |

### Supporting Files

| File | Purpose |
|---|---|
| `Dockerfile` | Backend container image |
| `docker-compose.yml` | Local development environment |
| `.env.example` | Environment variable template |
| `.gitignore` | Git exclusion patterns |

## 6.4 Parallel Execution

Tasks marked `[P]` are executed concurrently within their phase:

```markdown
### Phase 4: Frontend Pages

- [X] **Task 4.1**: Create Dashboard page [P]
- [X] **Task 4.2**: Create Details page [P]
- [X] **Task 4.3**: Create Budgets page [P]
- [X] **Task 4.4**: Create Login page [P]
```

{: .note }
> Parallel tasks target different files. The implement command ensures no write conflicts occur between concurrent tasks.

## 6.5 Error Handling

During implementation:

- **Sequential task failure** — Execution halts; error reported with context
- **Parallel task failure** — Other parallel tasks continue; failed task reported
- **Constitution violation** — Execution halts; justification required
- **File conflict** — Execution halts; manual resolution needed

## 6.6 Progress Monitoring

As tasks complete, `tasks.md` is updated in real-time:

```markdown
- [X] **Task 1.1**: Initialize backend project structure    ← Completed
- [X] **Task 1.2**: Initialize frontend project structure   ← Completed
- [ ] **Task 2.1**: Create ORM models                       ← In progress
- [ ] **Task 2.2**: Create Alembic migrations               ← Pending
```

## 6.7 Hands-On Exercise

1. Verify all prerequisite artifacts exist:
   - `spec.md` ✓
   - `plan.md` ✓
   - `data-model.md` ✓
   - `contracts/openapi.yaml` ✓
   - `tasks.md` ✓
2. Run the implement command:
   ```
   /speckit.implement
   ```
3. Observe the execution:
   - Watch tasks being marked `[X]` in `tasks.md`
   - Monitor file creation in the explorer
   - Note phase transitions in the chat output
4. After completion, verify the generated project:
   ```bash
   # Backend
   cd backend && pip install -r requirements.txt
   python -m pytest tests/

   # Frontend
   cd frontend && npm install && npm run build
   ```

## 6.8 Post-Implementation Validation

After all tasks complete, verify:

```bash
# Check all tasks marked complete
grep -c "\[X\]" specs/001-azure-cost-monitoring/tasks.md
# Expected: 88

# Verify project structure exists
find backend/ -name "*.py" | wc -l
find frontend/src -name "*.tsx" | wc -l
find infra/ -name "*.sh" | wc -l
```

## Checklist

Before proceeding to Module 7:

- ☐ `/speckit.implement` executed to completion
- ☐ All tasks marked `[X]` in `tasks.md`
- ☐ Backend code compiles without errors
- ☐ Frontend builds successfully
- ☐ Infrastructure scripts are syntactically valid
- ☐ Docker configuration files present

---

[← Task Generation](/Overview-Github-Spec-kit/modules/06-task-generation/) | [Next: Analysis & Review →](/Overview-Github-Spec-kit/modules/08-analysis-review/)
