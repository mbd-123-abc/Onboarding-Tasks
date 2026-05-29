# Repository Access Model

## Overview

This document describes the branch protection rules, access levels, and security configuration for this repository.

---

## Branch Protection Rules — `all branches`

The following ruleset is applied to all branches:

| Rule | Status | Description |
|------|--------|-------------|
| Block force pushes | ✅ Enabled | Prevents users with push access from force pushing to refs |
| Require review from Code Owners | ✅ Enabled | Requires an approving review on PRs that modify files with a designated code owner |
| Allowed merge methods | Merge, Rebase | Only merge and rebase commits are permitted; no squash merges |
| Require signed commits | ✅ Enabled | Commits pushed to matching refs must have verified signatures |
| Require a pull request before merging | ✅ Enabled | All changes must go through a pull request; no direct pushes to protected refs |
| Restrict updates | ✅ Enabled | Only users with bypass permission can update matching refs |
| Restrict deletions | ✅ Enabled | Only users with bypass permission can delete matching refs |
| Require linear history | ✅ Enabled | Merge commits are blocked; history must remain linear via merge or rebase |

---

## Bypass List

The following roles are exempt from the ruleset above:

| Entity | Type | Reason |
|--------|------|--------|
| Repository Admin | Role | Admins need the ability to perform emergency fixes, manage CI/CD pipelines, and maintain the repository without being blocked by standard PR workflows |

> **Note:** Bypass permissions should be used sparingly and only in exceptional circumstances (e.g. hotfixes, CI automation). All standard changes should still go through the normal PR process even for admins.

---

## Collaborator Access Levels

| Role | Who | What They Can Do |
|------|-----|-----------------|
| Admin | Repo owner, DevOps lead | Full control: manage settings, secrets, bypass rules, add/remove collaborators |
| Maintain | Tech leads | Manage issues, PRs, and repo settings; cannot change branch protection or secrets |
| Write | Developers | Push to non-protected branches, open and merge PRs (subject to rules above) |
| Triage | QA, support | Manage issues and PRs; cannot push code |
| Read | Stakeholders, auditors | View code and issues only |

---

## Deployment Protection Rules

Configured under **Settings → Environments → [Environment Name] → Protection Rules**.

| Rule | Status | Description |
|------|--------|-------------|
| Required reviewers | ✅ Enabled | Designated people or teams must approve workflow runs before deployment proceeds (up to 6 reviewers) |
| Prevent self-review | ✅ Enabled | The user who triggered the workflow run cannot be their own approver — a different reviewer is required |

### Required Reviewers

Add up to 6 people or teams who are authorized to approve deployments. Recommended setup:

| Reviewer | Type | Environment |
|----------|------|-------------|
| Repository Admin | Role | Production |
| Tech Lead | Team | Staging, Production |

> Reviewers are notified automatically when a workflow run is waiting for approval. They must approve before the deployment proceeds.

---

## Repository Secrets

Secrets are stored under **Settings → Secrets and Variables → Actions** and are never exposed in logs.

| Secret Name | Purpose |
|-------------|---------|
| `SECRET_NUM` | A secret number. |

Secrets are only accessible to workflow runs and users with Admin access.

---

## Why This Model

**Deployment protection rules with required reviewers** ensure no deployment reaches an environment without explicit human sign-off, preventing accidental or unauthorized releases.

**Prevent self-review** enforces a four-eyes principle — the person who triggers a deployment cannot also approve it, reducing the risk of a single person pushing unreviewed changes to production.

 ensures every change is reviewed before it reaches any branch, reducing bugs and unreviewed code.

**Code Owner reviews** guarantee that subject-matter experts sign off on changes to files they own, enforcing accountability.

**Linear history** keeps the commit log readable and makes rollbacks straightforward.

**Signed commits** verify that commits genuinely come from the stated author, protecting against spoofed contributions.

**Restrict updates and deletions** prevents accidental or unauthorized branch modifications outside of the PR process.

**Admin-only bypass** balances security with operational flexibility — one trusted role can act quickly in emergencies without the entire team being blocked.
