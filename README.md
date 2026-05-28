# 🚀 Awesome Workflows

A curated collection of **GitHub Action workflows** for repository management, triage, quality enforcement, and automation. Drop them into your `.github/workflows/` directory and adapt as needed.

---

## 📖 How to Use

1. Browse the index below and pick a workflow.
2. Check the **Portability** column:
   - ✅ **Drop-in** — Copy the file as-is; no repo-specific changes needed.
   - 🔧 **Configurable** — Works out of the box but you'll want to tweak values (labels, days, team names, etc.).
   - ⚙️ **Needs Setup** — Requires repo-specific secrets, tokens, project IDs, or external service configuration.
3. Copy the `.yml` file into your repository's `.github/workflows/` directory.
4. Commit, push, and you're done.

### 🔄 Manual Dispatch

Most workflows support **manual triggering** via `workflow_dispatch`. When run manually from the Actions tab, they review **all open issues/PRs** and apply their logic retroactively — useful for:
- First-time setup on an existing repo with a backlog
- Re-running checks after changing configuration values
- Periodic manual audits

---

## 📑 Workflow Index

### 🗂️ Issue Management

| # | Workflow | File | Description | Portability |
|---|---------|------|-------------|:-----------:|
| 1 | [Stale Issue & PR Closer](#1-stale-issue--pr-closer) | `stale-issues.yml` | Labels and closes issues/PRs that have been inactive for a configurable number of days. | 🔧 Configurable |
| 2 | [Auto-Label Issues by Keywords](#2-auto-label-issues-by-keywords) | `auto-label-issues.yml` | Scans issue titles and bodies for keywords and applies labels automatically (e.g., `bug`, `enhancement`, `docs`). | 🔧 Configurable |
| 3 | [Issue Template Checker](#3-issue-template-checker) | `issue-template-check.yml` | Verifies that new issues actually filled out the issue template instead of leaving it blank or deleting it. | 🔧 Configurable |
| 4 | [Needs Info Timeout](#4-needs-info-timeout) | `needs-info-timeout.yml` | When a `needs-info` label is added, posts a comment. If no reply after 14 days, auto-closes the issue. | 🔧 Configurable |
| 5 | [Lock Closed Threads](#5-lock-closed-threads) | `lock-threads.yml` | Locks issues and PRs that have been closed for 30+ days to prevent necro-bumping. | 🔧 Configurable |
| 6 | [Duplicate Issue Detector](#6-duplicate-issue-detector) | `duplicate-detector.yml` | Uses word-overlap similarity to detect potential duplicate issues and comments with links to the originals. | 🔧 Configurable |
| 7 | [Auto-Close Spam Issues](#7-auto-close-spam-issues) | `close-spam-issues.yml` | Detects issues that are likely spam (very short body, suspicious patterns) and closes them with a label. | ✅ Drop-in |
| 8 | [Issue Assigner on Comment](#8-issue-assigner-on-comment) | `issue-assign-on-comment.yml` | Allows contributors to self-assign issues by commenting `/assign`. Optionally limits assignments per user. | 🔧 Configurable |

### 🔀 Pull Request Management

| # | Workflow | File | Description | Portability |
|---|---------|------|-------------|:-----------:|
| 9 | [PR Issue Assignment Check](#9-pr-issue-assignment-check) | `pr-issue-check.yml` | Ensures every PR references an issue and that the PR author is assigned to it. Closes non-compliant PRs. | ✅ Drop-in |
| 10 | [PR Size Labeler](#10-pr-size-labeler) | `pr-size-labeler.yml` | Automatically labels PRs based on total lines changed (`size/XS` through `size/XXL`). | ✅ Drop-in |
| 11 | [PR Title Linter (Conventional Commits)](#11-pr-title-linter) | `pr-title-lint.yml` | Enforces Conventional Commit format on PR titles (e.g., `feat:`, `fix:`, `docs:`). | 🔧 Configurable |
| 12 | [Auto-Assign Reviewers](#12-auto-assign-reviewers) | `auto-assign-reviewers.yml` | Automatically assigns reviewers to new PRs using round-robin or random selection from a configured team. | ⚙️ Needs Setup |
| 13 | [WIP / Draft Enforcer](#13-wip--draft-enforcer) | `wip-enforcer.yml` | Fails CI if a PR title contains `[WIP]` or `WIP:` to prevent accidental merging of work-in-progress. | ✅ Drop-in |
| 14 | [PR Description Checklist Validator](#14-pr-description-checklist-validator) | `pr-checklist-check.yml` | Ensures all checklist items (`- [ ]`) in the PR template are checked before allowing merge. | ✅ Drop-in |
| 15 | [Auto-Label PRs by Path](#15-auto-label-prs-by-path) | `pr-path-labeler.yml` | Applies labels based on which files/directories a PR modifies (e.g., `frontend`, `backend`, `docs`). | 🔧 Configurable |
| 16 | [First-Time Contributor Welcome](#16-first-time-contributor-welcome) | `welcome-contributor.yml` | Posts a friendly welcome comment when a user opens their first issue or PR in the repository. | 🔧 Configurable |

### 🛡️ Security & Quality

| # | Workflow | File | Description | Portability |
|---|---------|------|-------------|:-----------:|
| 17 | [Secret Leak Scanner (Gitleaks)](#17-secret-leak-scanner) | `gitleaks-scan.yml` | Scans every PR for accidentally committed secrets, API keys, and credentials using Gitleaks. | ✅ Drop-in |
| 18 | [Dependency Review](#18-dependency-review) | `dependency-review.yml` | Checks PRs for newly added dependencies with known vulnerabilities before they are merged. | ✅ Drop-in |
| 19 | [Auto-Merge Dependabot PRs](#19-auto-merge-dependabot-prs) | `dependabot-auto-merge.yml` | Automatically merges Dependabot PRs for patch/minor version bumps after CI passes. | 🔧 Configurable |
| 20 | [License Compliance Check](#20-license-compliance-check) | `license-check.yml` | Scans dependencies and ensures no incompatible licenses (e.g., GPL in an MIT project) are introduced. | 🔧 Configurable |
| 21 | [CODEOWNERS Validator](#21-codeowners-validator) | `codeowners-validator.yml` | Validates that the `CODEOWNERS` file references only existing users/teams and has no syntax errors. | ✅ Drop-in |

### 📦 Release & Changelog

| # | Workflow | File | Description | Portability |
|---|---------|------|-------------|:-----------:|
| 22 | [Release Drafter](#22-release-drafter) | `release-drafter.yml` | Automatically drafts GitHub Releases by categorizing merged PRs by their labels into a changelog. | 🔧 Configurable |
| 23 | [Auto-Tag on Merge](#23-auto-tag-on-merge) | `auto-tag.yml` | Creates a new Git tag when a version bump is detected in a config file (e.g., `package.json`, `pyproject.toml`). | 🔧 Configurable |
| 24 | [Publish Release on Tag](#24-publish-release-on-tag) | `publish-release.yml` | Creates a GitHub Release with auto-generated notes whenever a new version tag is pushed. | ✅ Drop-in |

### 🧹 Repository Hygiene

| # | Workflow | File | Description | Portability |
|---|---------|------|-------------|:-----------:|
| 25 | [Branch Cleanup](#25-branch-cleanup) | `branch-cleanup.yml` | Deletes branches that have been merged or are stale (no commits for 90+ days). | 🔧 Configurable |
| 26 | [Old Workflow Run Cleanup](#26-old-workflow-run-cleanup) | `cleanup-workflow-runs.yml` | Periodically deletes old workflow run logs and artifacts to save storage. | 🔧 Configurable |
| 27 | [Broken Link Checker](#27-broken-link-checker) | `broken-links.yml` | Scans all markdown files in the repository for broken links (404s) on a weekly schedule. | ✅ Drop-in |
| 28 | [TODO/FIXME Tracker](#28-todofixme-tracker) | `todo-tracker.yml` | Scans PRs for new `TODO` or `FIXME` comments and posts a summary comment on the PR. | ✅ Drop-in |

### 📊 Reporting & Notifications

| # | Workflow | File | Description | Portability |
|---|---------|------|-------------|:-----------:|
| 29 | [Weekly Activity Digest](#29-weekly-activity-digest) | `weekly-digest.yml` | Generates a weekly summary of issues opened/closed, PRs merged, and contributors, posted to Slack/Discord. | ⚙️ Needs Setup |
| 30 | [Add Issues/PRs to Project Board](#30-add-issuesprs-to-project-board) | `add-to-project.yml` | Automatically adds new issues and PRs to a specified GitHub Project board. | ⚙️ Needs Setup |

---

## 📝 Workflow Details

### 🗂️ Issue Management

#### 1. Stale Issue & PR Closer
> Uses [`actions/stale`](https://github.com/actions/stale) to automatically label and close inactive issues and PRs.

- **Trigger:** Scheduled (daily cron) + `workflow_dispatch`
- **What it does:** Marks issues/PRs as `stale` after 60 days of inactivity, closes them after 14 more days.
- **Manual dispatch:** Runs the same stale-check logic immediately on demand.
- **Portability:** 🔧 Customize `days-before-stale`, `days-before-close`, messages, and exempt labels.

---

#### 2. Auto-Label Issues by Keywords
> Scans issue titles and body content for configurable keywords and applies matching labels.

- **Trigger:** `issues: [opened, edited]` + `workflow_dispatch`
- **What it does:** If the title/body contains "bug" or "error" → applies `bug` label; "feature" or "enhancement" → `enhancement`, etc.
- **Manual dispatch:** Reviews all open issues and applies any missing labels.
- **Portability:** 🔧 Edit the keyword-to-label mapping to match your label taxonomy.

---

#### 3. Issue Template Checker
> Validates that new issues contain meaningful content from the issue template.

- **Trigger:** `issues: [opened]` + `workflow_dispatch`
- **What it does:** Checks if the issue body meets a minimum length and contains expected template sections. Comments and applies a `needs-more-info` label if not.
- **Manual dispatch:** Reviews all open issues for template compliance. Skips already-labeled issues.
- **Portability:** 🔧 Adjust minimum body length and required section headers.

---

#### 4. Needs Info Timeout
> Auto-closes issues that haven't received a response after being marked `needs-info`.

- **Trigger:** Scheduled (daily cron) + `workflow_dispatch`
- **What it does:** Finds issues labeled `needs-info` with no author reply for 14 days, posts a reminder, then closes.
- **Manual dispatch:** Runs the same timeout check immediately on demand.
- **Portability:** 🔧 Adjust the label name and timeout period.

---

#### 5. Lock Closed Threads
> Uses [`dessant/lock-threads`](https://github.com/dessant/lock-threads) to lock old closed issues.

- **Trigger:** Scheduled (daily cron) + `workflow_dispatch`
- **What it does:** Locks issues/PRs that have been closed for 30+ days to prevent necro-bumping.
- **Manual dispatch:** Runs the same lock check immediately on demand.
- **Portability:** 🔧 Adjust `issue-inactive-days` and lock reason message.

---

#### 6. Duplicate Issue Detector
> Uses word-overlap (Jaccard) similarity to detect potential duplicate issues. No external APIs required.

- **Trigger:** `issues: [opened]` + `workflow_dispatch`
- **What it does:** Tokenizes and compares new issues against all open issues using Jaccard similarity with stop-word removal. Comments with links to potential duplicates and labels them `possible-duplicate`.
- **Manual dispatch:** Cross-compares all open issues against each other. Skips already-flagged issues.
- **Portability:** 🔧 Adjust `SIMILARITY_THRESHOLD` (0.0–1.0) and `MAX_RESULTS`. For better semantic matching, swap in an AI-based approach.

---

#### 7. Auto-Close Spam Issues
> Detects and closes obviously spam or empty issues.

- **Trigger:** `issues: [opened]` + `workflow_dispatch`
- **What it does:** Checks if the issue body is extremely short (< 10 chars), contains known spam patterns, or has no body at all. Applies a `spam` label and closes.
- **Manual dispatch:** Reviews all open issues for spam. Skips already-labeled spam issues.
- **Portability:** ✅ Works as-is. Can optionally tune spam patterns.

---

#### 8. Issue Assigner on Comment
> Allows contributors to self-assign issues by commenting `/assign`.

- **Trigger:** `issue_comment: [created]`
- **What it does:** When a user comments `/assign` on an issue, the workflow assigns them. Optionally limits max open assignments per contributor.
- **Portability:** 🔧 Adjust the max assignment limit.

---

### 🔀 Pull Request Management

#### 9. PR Issue Assignment Check
> Ensures PRs reference an issue and the author is assigned to it.

- **Trigger:** `pull_request: [opened, edited, reopened]` + `workflow_dispatch`
- **What it does:** Parses the PR body for issue references (`#123`), verifies they exist, and checks if the PR author is assigned. Closes non-compliant PRs with a comment.
- **Manual dispatch:** Reviews all open PRs for issue-assignment compliance.
- **Portability:** ✅ Works as-is for any repository.

---

#### 10. PR Size Labeler
> Automatically labels PRs by the number of lines changed.

- **Trigger:** `pull_request: [opened, synchronize]` + `workflow_dispatch`
- **What it does:** Adds a label like `size/XS` (< 10 lines), `size/S` (< 50), `size/M` (< 200), `size/L` (< 500), `size/XL` (< 1000), or `size/XXL` (1000+). Updates labels when PR size changes.
- **Manual dispatch:** Reviews all open PRs and applies/updates size labels.
- **Portability:** ✅ Works as-is. Change thresholds if desired.

---

#### 11. PR Title Linter
> Enforces [Conventional Commits](https://www.conventionalcommits.org/) format on PR titles.

- **Trigger:** `pull_request: [opened, edited, reopened]` + `workflow_dispatch`
- **What it does:** Validates that the PR title matches `type(scope): description` format. Fails the check if it doesn't. Avoids duplicate comments.
- **Manual dispatch:** Reviews all open PRs for title compliance. Reports total failures.
- **Portability:** 🔧 Configure allowed types (`feat`, `fix`, `docs`, `chore`, etc.) and whether scope is required.

---

#### 12. Auto-Assign Reviewers
> Automatically assigns reviewers to new PRs.

- **Trigger:** `pull_request: [opened, ready_for_review]` + `workflow_dispatch`
- **What it does:** Picks reviewers from a configured list using round-robin selection. Skips the PR author and draft PRs.
- **Manual dispatch:** Assigns reviewers to all open PRs that are missing reviewers.
- **Portability:** ⚙️ Requires a list of reviewer usernames and possibly a PAT for team-based assignment.

---

#### 13. WIP / Draft Enforcer
> Prevents accidental merging of work-in-progress PRs.

- **Trigger:** `pull_request: [opened, edited, reopened, synchronize]` + `workflow_dispatch`
- **What it does:** Fails the CI check if the PR title starts with `[WIP]`, `WIP:`, or `Draft:`. Also detects the 🚧 emoji.
- **Manual dispatch:** Lists all open WIP PRs (informational, does not fail).
- **Portability:** ✅ Works as-is.

---

#### 14. PR Description Checklist Validator
> Ensures all checkboxes in the PR template are checked.

- **Trigger:** `pull_request: [opened, edited, reopened]` + `workflow_dispatch`
- **What it does:** Parses the PR body for unchecked boxes (`- [ ]`). Fails the check if any remain unchecked, with a helpful comment listing what's missing. Avoids duplicate comments.
- **Manual dispatch:** Reviews all open PRs and reports which have incomplete checklists.
- **Portability:** ✅ Works for any repo that uses a PR template with checklists.

---

#### 15. Auto-Label PRs by Path
> Labels PRs based on which files/directories were modified using an inline path-to-label mapping.

- **Trigger:** `pull_request: [opened, synchronize]` + `workflow_dispatch`
- **What it does:** Applies labels based on file paths (e.g., changes to `docs/` → `documentation`, changes to `src/api/` → `backend`). Config is inline — no separate file needed.
- **Manual dispatch:** Reviews all open PRs and applies any missing path-based labels.
- **Portability:** 🔧 Edit the `PATH_LABELS` mapping in the workflow to match your project structure.

---

#### 16. First-Time Contributor Welcome
> Posts a welcome message for first-time contributors.

- **Trigger:** `issues: [opened]`, `pull_request_target: [opened]`
- **What it does:** Detects if this is the user's first issue or PR in the repo and posts a customizable welcome comment.
- **Portability:** 🔧 Customize the welcome messages. Optionally link to your `CONTRIBUTING.md`.

---

### 🛡️ Security & Quality

#### 17. Secret Leak Scanner
> Uses [Gitleaks](https://github.com/gitleaks/gitleaks-action) to scan for secrets in code.

- **Trigger:** `pull_request` and `push` to main
- **What it does:** Scans diffs for API keys, tokens, passwords, and other secrets. Fails the check if any are found.
- **Portability:** ✅ Works as-is. Optionally add a `.gitleaks.toml` for custom rules/allowlists.

---

#### 18. Dependency Review
> Uses [`actions/dependency-review-action`](https://github.com/actions/dependency-review-action) to catch vulnerable dependencies.

- **Trigger:** `pull_request`
- **What it does:** Reviews dependency changes in PRs and fails if any newly added dependency has known vulnerabilities.
- **Portability:** ✅ Works for any repo using npm, pip, Maven, Go modules, etc.

---

#### 19. Auto-Merge Dependabot PRs
> Automatically merges safe Dependabot version bumps.

- **Trigger:** `pull_request`
- **What it does:** If the PR is opened by `dependabot[bot]` and is a patch or minor update, enables auto-merge after CI passes.
- **Portability:** 🔧 Requires "Allow auto-merge" enabled in repo settings. Adjust to restrict to patch-only if desired.

---

#### 20. License Compliance Check
> Scans dependencies for incompatible licenses.

- **Trigger:** `pull_request`
- **What it does:** Checks all direct and transitive dependencies for license compatibility. Fails if a restrictive license (e.g., GPL) is found in a permissively-licensed project.
- **Portability:** 🔧 Configure the list of allowed/denied licenses for your project.

---

#### 21. CODEOWNERS Validator
> Validates the `CODEOWNERS` file for correctness.

- **Trigger:** `pull_request` (when `CODEOWNERS` is modified)
- **What it does:** Checks that all referenced users/teams exist and file patterns are syntactically valid.
- **Portability:** ✅ Works for any repo with a `CODEOWNERS` file.

---

### 📦 Release & Changelog

#### 22. Release Drafter
> Uses [`release-drafter/release-drafter`](https://github.com/release-drafter/release-drafter) to auto-generate changelogs.

- **Trigger:** `push` to main
- **What it does:** Categorizes merged PRs by label (`feature`, `bug`, `chore`) and continuously updates a draft GitHub Release.
- **Portability:** 🔧 Requires a `.github/release-drafter.yml` config to define label categories and version resolution.

---

#### 23. Auto-Tag on Merge
> Creates a Git tag when a version change is detected.

- **Trigger:** `push` to main
- **What it does:** Reads the version from `package.json`, `pyproject.toml`, or similar, and creates a tag (e.g., `v1.2.3`) if it changed.
- **Portability:** 🔧 Configure which file to read the version from.

---

#### 24. Publish Release on Tag
> Creates a GitHub Release when a new tag is pushed.

- **Trigger:** `push` tags matching `v*`
- **What it does:** Generates release notes from commits since the last tag and creates a formal GitHub Release.
- **Portability:** ✅ Works as-is for any repo using semver tags.

---

### 🧹 Repository Hygiene

#### 25. Branch Cleanup
> Deletes merged and stale branches.

- **Trigger:** `pull_request: [closed]` and scheduled (weekly cron)
- **What it does:** Deletes head branches after PR merge. On schedule, also finds and deletes branches with no activity for 90+ days.
- **Portability:** 🔧 Adjust the staleness threshold and protected branch patterns.

---

#### 26. Old Workflow Run Cleanup
> Cleans up old workflow run logs and artifacts.

- **Trigger:** Scheduled (weekly cron)
- **What it does:** Deletes workflow runs older than a configurable number of days. Helps save storage on active repositories.
- **Portability:** 🔧 Adjust the retention period (default: 30 days).

---

#### 27. Broken Link Checker
> Scans markdown files for broken links.

- **Trigger:** Scheduled (weekly cron) and `push` to main
- **What it does:** Crawls all `.md` files in the repository and reports any links that return 404 or fail to resolve.
- **Portability:** ✅ Works as-is.

---

#### 28. TODO/FIXME Tracker
> Surfaces new TODO/FIXME comments introduced in PRs.

- **Trigger:** `pull_request`
- **What it does:** Diffs the PR and finds any new `TODO`, `FIXME`, `HACK`, or `XXX` comments. Posts a summary comment on the PR.
- **Portability:** ✅ Works as-is. Optionally customize which keywords to track.

---

### 📊 Reporting & Notifications

#### 29. Weekly Activity Digest
> Posts a weekly summary of repository activity to Slack or Discord.

- **Trigger:** Scheduled (weekly cron — Fridays)
- **What it does:** Queries the GitHub API for issues opened/closed, PRs merged, new contributors, and formats a digest sent via webhook.
- **Portability:** ⚙️ Requires a Slack or Discord webhook URL stored as a repository secret.

---

#### 30. Add Issues/PRs to Project Board
> Uses [`actions/add-to-project`](https://github.com/actions/add-to-project) to auto-populate Project boards.

- **Trigger:** `issues: [opened]` and `pull_request: [opened]`
- **What it does:** Automatically adds every new issue and PR to a specified GitHub Projects (v2) board.
- **Portability:** ⚙️ Requires the Project ID/URL and a PAT with `project` scope.

---

## 🏷️ Portability Legend

| Icon | Meaning | What You Need to Do |
|:----:|---------|---------------------|
| ✅ | **Drop-in** | Copy the file, commit, done. No changes required. |
| 🔧 | **Configurable** | Works immediately but review the config values (timeouts, labels, thresholds) and adjust to your preferences. |
| ⚙️ | **Needs Setup** | Requires external configuration: API keys, webhook URLs, PATs, Project IDs, or third-party service accounts. |

---

## 📂 Repository Structure

```
awesome-workflows/
├── README.md
└── github-actions/
    ├── stale-issues.yml
    ├── auto-label-issues.yml
    ├── issue-template-check.yml
    ├── needs-info-timeout.yml
    ├── lock-threads.yml
    ├── duplicate-detector.yml
    ├── close-spam-issues.yml
    ├── issue-assign-on-comment.yml
    ├── pr-issue-check.yml
    ├── pr-size-labeler.yml
    ├── pr-title-lint.yml
    ├── auto-assign-reviewers.yml
    ├── wip-enforcer.yml
    ├── pr-checklist-check.yml
    ├── pr-path-labeler.yml
    ├── welcome-contributor.yml
    ├── gitleaks-scan.yml
    ├── dependency-review.yml
    ├── dependabot-auto-merge.yml
    ├── license-check.yml
    ├── codeowners-validator.yml
    ├── release-drafter.yml
    ├── auto-tag.yml
    ├── publish-release.yml
    ├── branch-cleanup.yml
    ├── cleanup-workflow-runs.yml
    ├── broken-links.yml
    ├── todo-tracker.yml
    ├── weekly-digest.yml
    └── add-to-project.yml
```

---

## 🤝 Contributing

Found a useful workflow? Feel free to open a PR! Please ensure:
- The workflow file is well-commented.
- You add an entry to the index table and details section in this README.
- You mark the correct portability level.

## 📄 License

This project is licensed under the [MIT License](LICENSE).
