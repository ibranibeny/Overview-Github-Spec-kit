---
layout: default
title: "Step 2: Clarify"
parent: Demo Walkthrough
nav_order: 2
permalink: /demo/step-2-clarify/
---

# Step 2 — Clarify Requirements
{: .no_toc }

Resolve ambiguities and underspecified areas in the feature specification.
{: .fs-6 .fw-300 }

<details open markdown="block">
  <summary>Table of Contents</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## 2.1 Run the Clarify Command

```text
/speckit.clarify
```

Spec-kit analyzes the specification and asks up to **5 targeted questions** about areas that need more precision.

## 2.2 Clarification Questions (Example)

The following questions were generated for the Azure Cost Monitoring Tool:

| # | Question | Purpose |
|---|---|---|
| 1 | Should authentication use Azure AD SSO or a local credential store? | Determines auth complexity |
| 2 | What is the data retention period for historical cost records? | Impacts storage design |
| 3 | Should budget alerts trigger email notifications or in-app only? | Scopes alert delivery |
| 4 | Is multi-subscription support needed from day one? | Determines query scope |
| 5 | Should the anomaly detection threshold be configurable per user? | Defines flexibility |

## 2.3 Providing Answers

Respond directly to each question:

```text
1. Static login with local credentials (bcrypt). No Azure AD.
2. 12 months rolling retention.
3. In-app alerts only for now. Email is out of scope.
4. Single subscription initially, but schema should be multi-sub ready.
5. Fixed threshold (2σ over 7-day average). Not configurable per user.
```

## 2.4 What Happens Next

Spec-kit **encodes your answers back into the spec**, updating:

- Authentication section → "Static login, bcrypt, JWT tokens"
- Data retention → "12 months rolling, older records purged"
- Alerts → "In-app notification only"
- Scope → "Single subscription, multi-sub ready schema"
- Anomaly → "Fixed 2σ threshold, 7-day rolling average"

## 2.5 Before vs After Clarification

| Area | Before | After |
|---|---|---|
| Auth Model | "Users must be authenticated" | "Static login, bcrypt, JWT (1h access / 7d refresh)" |
| Retention | Not specified | "12 months rolling, daily purge job" |
| Alerts | "Alert when budget exceeded" | "In-app only, banner + alerts page" |
| Scope | "Monitor Azure costs" | "Single subscription, multi-sub ready" |
| Anomaly | "Highlight anomalies" | "2σ over 7-day rolling baseline, fixed" |

{: .tip }
> Clarification eliminates assumptions early. Without this step, the planning phase would need to make arbitrary decisions that may not match your intent.

## 2.6 Output

The same `spec.md` file is updated in place with clarified requirements. No new files are created.

```text
specs/001-azure-cost-monitoring/
└── spec.md              ← Updated with clarification answers
```

---

[← Step 1: Specify](/Overview-Github-Spec-kit/demo/step-1-specify/) | [Next: Generate the Plan →](/Overview-Github-Spec-kit/demo/step-3-plan/)
