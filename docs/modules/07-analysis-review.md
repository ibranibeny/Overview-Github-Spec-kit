---
layout: default
title: 7. Analysis & Review
nav_order: 8
permalink: /modules/07-analysis-review/
---

# Module 7 — Analysis & Review
{: .no_toc }

Validate cross-artifact consistency and quality using `/speckit.analyze`, then iterate on any findings.
{: .fs-6 .fw-300 }

<details open markdown="block">
  <summary>Table of Contents</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## 7.1 The Analyze Command

The `/speckit.analyze` command performs a non-destructive consistency and quality analysis across all Spec-kit artifacts:

```
/speckit.analyze
```

## 7.2 What Gets Analyzed

The analysis validates relationships between:

| Artifact Pair | Validation |
|---|---|
| spec.md ↔ plan.md | All spec requirements addressed in plan |
| plan.md ↔ tasks.md | All plan components have corresponding tasks |
| data-model.md ↔ contracts/ | API endpoints match entity schema |
| tasks.md ↔ source code | All tasks produced expected files |
| constitution ↔ plan.md | All principles satisfied |

## 7.3 Analysis Report

The output includes a structured report:

```markdown
## Cross-Artifact Consistency Report

### Spec → Plan Coverage
✅ All 12 functional requirements mapped to plan sections
✅ All 5 non-functional requirements have implementation strategy
⚠️  1 acceptance criterion lacks explicit task mapping

### Plan → Tasks Coverage
✅ All backend components have tasks (23/23)
✅ All frontend components have tasks (18/18)
✅ All infrastructure scripts have tasks (6/6)
⚠️  1 testing task references undefined fixture

### Constitution Compliance
✅ PaaS-First: No VM or AKS references in implementation
✅ Hub-Spoke: Network scripts implement correct topology
✅ Auth Model: JWT implementation matches specification
```

## 7.4 Common Findings

| Finding Type | Severity | Action |
|---|---|---|
| Missing test coverage | Warning | Add tests for uncovered endpoints |
| Unused API endpoint | Info | Remove from contract or implement |
| Inconsistent naming | Warning | Align with plan conventions |
| Missing error handling | Warning | Add to affected services |
| Constitution drift | Error | Justify or fix implementation |

## 7.5 Iteration Workflow

When the analysis identifies issues:

1. **Review findings** — Determine which require action
2. **Update artifacts** — Fix spec, plan, or tasks as needed
3. **Re-implement** — Run `/speckit.implement` for affected tasks only
4. **Re-analyze** — Confirm issues resolved

{: .tip }
> Minor warnings (e.g., missing comments, optional documentation) do not block deployment. Focus on errors and consistency violations.

## 7.6 Quality Metrics

After a successful implementation, expect:

| Metric | Target | Description |
|---|---|---|
| Spec Coverage | 100% | All requirements have tasks |
| Task Completion | 100% | All tasks marked `[X]` |
| Constitution Pass | 100% | All principles validated |
| File Alignment | >95% | Generated files match plan structure |
| API Contract Match | 100% | Endpoints match OpenAPI spec |

## 7.7 Additional Commands

| Command | Purpose |
|---|---|
| `/speckit.checklist` | Generate quality checklists (UX, security, testing) |
| `/speckit.git.commit` | Commit all changes with auto-generated message |
| `/speckit.taskstoissues` | Convert remaining tasks to GitHub Issues |

## 7.8 Hands-On Exercise

1. Run the analysis command:
   ```
   /speckit.analyze
   ```
2. Review the consistency report
3. Address any ⚠️ warnings or ❌ errors:
   - Update affected files
   - Re-run specific tasks if needed
4. Run analysis again to confirm resolution
5. Commit the final state:
   ```
   /speckit.git.commit
   ```

## 7.9 Workshop Summary

Congratulations! You have completed the full Spec-kit workflow:

| Stage | Command | Status |
|---|---|---|
| Constitution | `/speckit.constitution` | ✅ Principles defined |
| Specification | `/speckit.specify` | ✅ Feature spec created |
| Clarification | `/speckit.clarify` | ✅ Ambiguities resolved |
| Planning | `/speckit.plan` | ✅ Architecture designed |
| Task Generation | `/speckit.tasks` | ✅ 88 tasks generated |
| Implementation | `/speckit.implement` | ✅ All code produced |
| Analysis | `/speckit.analyze` | ✅ Consistency validated |

{: .note }
> The complete Azure Cost Monitoring Tool — with backend, frontend, infrastructure, and tests — was generated from a single natural language description in under 2 hours.

## Checklist

Workshop completion:

- ☐ `/speckit.analyze` executed successfully
- ☐ Consistency report reviewed
- ☐ Any critical findings addressed
- ☐ Final code committed to repository
- ☐ Understanding of the full Spec-kit pipeline confirmed

---

[← Implementation]({{ site.baseurl }}{% link modules/06-implementation.md %}) | [Back to Home]({{ site.baseurl }}/)
