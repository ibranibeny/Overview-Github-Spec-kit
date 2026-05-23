---
layout: default
title: 1. Prerequisites
nav_order: 2
permalink: /modules/01-prerequisites/
---

# Module 1 — Prerequisites
{: .no_toc }

Set up your local environment and verify all required tools before beginning the workshop.
{: .fs-6 .fw-300 }

<details open markdown="block">
  <summary>Table of Contents</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## 1.1 Visual Studio Code

You need VS Code with the following extensions installed:

| Extension | Required Version | Purpose |
|---|---|---|
| VS Code | 1.96+ | IDE |
| GitHub Copilot | Latest | AI code generation |
| GitHub Copilot Chat | Latest | Agent mode & chat |
| Spec-kit Extension | Latest | Workflow commands |

### Install VS Code

Download from [code.visualstudio.com](https://code.visualstudio.com/) or via CLI:

```bash
# Windows (winget)
winget install Microsoft.VisualStudioCode

# macOS (brew)
brew install --cask visual-studio-code
```

## 1.2 GitHub Copilot Subscription

A valid GitHub Copilot subscription is required (Individual, Business, or Enterprise).

{: .warning }
> GitHub Copilot **Free** tier has limited agent mode access. Ensure you have an active **Pro** or **Business** subscription for full functionality.

### Verify Copilot Access

1. Open VS Code
2. Open the Copilot Chat panel (`Ctrl+Shift+I` / `Cmd+Shift+I`)
3. Type a message — if you receive a response, Copilot is active

## 1.3 Git

Git 2.30+ is required for repository management and feature branching.

```bash
git --version
# Expected: git version 2.30+
```

### Configure Git Identity

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

## 1.4 Node.js and Python

The demonstration project requires both runtimes:

| Runtime | Version | Purpose |
|---|---|---|
| Node.js | 18+ | Frontend (React + Vite) |
| Python | 3.11+ | Backend (FastAPI) |

### Verify Installation

```bash
node --version
# Expected: v18.x or higher

python --version
# Expected: Python 3.11+
```

{: .tip }
> Use [nvm](https://github.com/nvm-sh/nvm) (Node) and [pyenv](https://github.com/pyenv/pyenv) (Python) for managing multiple runtime versions.

## 1.5 Azure CLI (Optional)

If you intend to deploy the generated project to Azure, install the Azure CLI:

```bash
# Verify
az version

# Login
az login
az account set --subscription "<YOUR_SUBSCRIPTION_ID>"
```

{: .note }
> Azure deployment is optional for this workshop. The Spec-kit workflow itself does not require Azure access — only the demonstration project's infrastructure scripts do.

## 1.6 Workshop Repository

Clone or create a new workspace for the workshop:

```bash
mkdir speckit-workshop && cd speckit-workshop
git init
```

Alternatively, start with an empty VS Code workspace:

1. Open VS Code
2. **File** → **Open Folder** → Select or create a new empty folder
3. Open the integrated terminal (`Ctrl+`` `)

## Checklist

Before proceeding to Module 2:

- ☐ VS Code installed with latest version
- ☐ GitHub Copilot extension installed and active
- ☐ GitHub Copilot Chat extension installed
- ☐ Git 2.30+ installed and configured
- ☐ Node.js 18+ installed
- ☐ Python 3.11+ installed
- ☐ Empty workspace created

---

[Next: Spec-kit Overview →](/Overview-Github-Spec-kit/modules/02-speckit-overview/)
