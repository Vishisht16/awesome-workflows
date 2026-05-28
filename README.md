# Awesome Workflows

A curated, ready-to-use collection of **CI/CD workflow files** for multiple platforms. Each workflow is well-documented, battle-tested, and designed to be dropped into your project with minimal configuration.

---

## What's Inside

This repository organizes workflows by **platform** and **use case**. Browse the directory that matches your stack:

### Platforms

| Platform | Directory | Status |
|----------|-----------|--------|
| **GitHub Actions** | [`github-actions/`](github-actions/) | Active |
| **GitLab CI** | `gitlab-ci/` | Coming Soon |
| **Azure Pipelines** | `azure-pipelines/` | Coming Soon |
| **Bitbucket Pipelines** | `bitbucket-pipelines/` | Coming Soon |

### Use Cases

| Category | Description | Available For |
|----------|-------------|---------------|
| **Repo Management** | Issue triage, PR enforcement, labeling, stale cleanup, contributor onboarding | [GitHub Actions](github-actions/repo-management/) |
| **CI/CD** | Build, test, lint, deploy pipelines | Coming Soon |
| **Security** | Secret scanning, dependency audits, license compliance | Coming Soon |
| **Release** | Changelog generation, auto-tagging, release drafting | Coming Soon |

---

## How to Use

1. **Navigate** to the platform and category you need.
2. **Read the README** inside that directory -- it has a full index, portability ratings, and detailed docs for each workflow.
3. **Copy** the `.yml` file(s) into your project's CI/CD config directory (e.g., `.github/workflows/` for GitHub Actions).
4. **Customize** if needed -- each file has clear comments marking what to change.

### Portability Ratings

Every workflow is tagged with a portability level so you know what to expect:

| Icon | Level | Meaning |
|:----:|-------|---------|
| [D] | **Drop-in** | Copy the file, commit, done. Zero changes required. |
| [C] | **Configurable** | Works immediately but review the config values (timeouts, labels, thresholds). |
| [S] | **Needs Setup** | Requires secrets, API keys, webhook URLs, or external service configuration. |

---

## Repository Structure

```
awesome-workflows/
├── README.md                          <-- You are here
├── github-actions/
│   └── repo-management/
│       ├── README.md                  <-- Full index & docs for 30+ workflows
│       ├── stale-issues.yml
│       ├── auto-label-issues.yml
│       ├── pr-issue-check.yml
│       └── ...
├── gitlab-ci/                         <-- Coming soon
├── azure-pipelines/                   <-- Coming soon
└── bitbucket-pipelines/               <-- Coming soon
```

---

## Contributing

Contributions are welcome! To add a new workflow:

1. Place it in the correct `platform/category/` directory.
2. Add clear comments at the top of the file explaining what it does, its portability level, and what to customize.
3. Update the category's `README.md` with an index entry and a details section.
4. Open a PR with a descriptive title.

## License

This project is licensed under the [MIT License](LICENSE).
