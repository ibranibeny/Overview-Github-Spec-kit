---
layout: default
title: 6. Task Generation
nav_order: 7
permalink: /modules/06-task-generation/
---

# Module 6 — Task Generation
{: .no_toc }

Generate an actionable, dependency-ordered task list from the implementation plan using `/speckit.tasks`.
{: .fs-6 .fw-300 }

<details open markdown="block">
  <summary>Table of Contents</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## 5.1 The Tasks Command

The `/speckit.tasks` command reads your `plan.md`, `data-model.md`, and `contracts/` to produce a complete `tasks.md` — a dependency-ordered execution plan:

```
/speckit.tasks
```

## 5.2 Task Structure

Each task in `tasks.md` follows a consistent format:

```markdown
### Phase 1: Project Setup

- [ ] **Task 1.1**: Initialize backend project structure
  - Create `backend/` directory with FastAPI project layout
  - Files: `backend/app/__init__.py`, `backend/app/main.py`, `backend/requirements.txt`
  - Dependencies: None

- [ ] **Task 1.2**: Initialize frontend project structure [P]
  - Scaffold React + Vite + TypeScript project
  - Files: `frontend/package.json`, `frontend/vite.config.ts`, `frontend/src/App.tsx`
  - Dependencies: None
```

{: .note }
> Tasks marked with `[P]` can execute in **parallel** with other `[P]` tasks in the same phase. Sequential tasks must complete before the next begins.

## 5.3 Task Phases

The generated task list is organized into logical phases:

| Phase | Focus | Typical Tasks |
|---|---|---|
| **1. Setup** | Project scaffolding | Directory structure, dependencies, configs |
| **2. Data Layer** | Database & models | ORM models, migrations, seed data |
| **3. Core Backend** | Business logic | Services, API endpoints, authentication |
| **4. Frontend** | User interface | Pages, components, API integration |
| **5. Infrastructure** | Deployment scripts | Azure CLI scripts, Docker configs |
| **6. Integration** | Connecting layers | Middleware, logging, error handling |
| **7. Testing** | Quality assurance | Unit tests, integration tests |
| **8. Polish** | Final touches | Documentation, optimization |

## 5.4 Task Metadata

Each task includes metadata for execution:

| Field | Purpose | Example |
|---|---|---|
| **ID** | Unique identifier | `Task 3.4` |
| **Description** | What to implement | "Create cost aggregation service" |
| **Files** | Target file paths | `backend/app/services/cost_service.py` |
| **Dependencies** | Required prior tasks | `Task 2.1, Task 2.3` |
| **Parallel** | Can run concurrently | `[P]` marker |

## 5.5 Scale Example

For the Azure Cost Monitoring Tool, the task generation produced:

| Metric | Value |
|---|---|
| Total Tasks | 88 |
| Phases | 8 |
| Parallel Groups | 12 |
| Files Created | 60+ |
| Lines of Code | ~8,000 |

## 5.6 Dependency Resolution

Tasks are ordered to ensure prerequisites are met:

```
Task 1.1 (Init backend) ──┐
                           ├──→ Task 2.1 (ORM models)
Task 1.2 (Init frontend) ─┘         │
                                     ▼
                              Task 3.1 (Auth service)
                                     │
                              Task 3.2 (Cost service)
                                     │
                              Task 4.1 (Dashboard page)
```

{: .warning }
> Do not manually reorder tasks unless you understand the dependency chain. Out-of-order execution may produce broken code.

## 5.7 Hands-On Exercise

1. Ensure `plan.md` and supporting artifacts exist from Module 4
2. Run the tasks command:
   ```
   /speckit.tasks
   ```
3. Review the generated `tasks.md`:
   - Verify phase organization
   - Check dependency chains
   - Identify parallel task groups `[P]`
   - Count total tasks
4. Optionally generate checklists:
   ```
   /speckit.checklist
   ```

## 5.8 Task Validation

Before proceeding to implementation, verify:

- All file paths in tasks reference the structure defined in `plan.md`
- No circular dependencies exist
- Parallel tasks do not modify the same files
- Each task is atomic (can be completed independently)

## Checklist

Before proceeding to Module 6:

- ☐ `/speckit.tasks` executed successfully
- ☐ `tasks.md` generated with all phases
- ☐ Dependencies are logical and ordered correctly
- ☐ Parallel tasks identified with `[P]` markers
- ☐ All file paths align with `plan.md` project structure
- ☐ Task count and scope reviewed

---

[← Planning](/Overview-Github-Spec-kit/modules/05-planning/) | [Next: Implementation →](/Overview-Github-Spec-kit/modules/07-implementation/)
