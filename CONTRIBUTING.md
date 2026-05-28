# Contributing to Awesome Workflows

First off, thank you for considering contributing to Awesome Workflows! This project is community-driven, and we welcome contributions of all kinds, whether it's submitting a new workflow, fixing a bug, or improving documentation.

By participating in this project, you agree to abide by our [Code of Conduct](CODE_OF_CONDUCT.md).

---

## How Can I Contribute?

### 1. Submitting a New Workflow
Have a great workflow that other repositories could benefit from? We'd love to add it!

**Steps to add a new workflow:**
1. Determine the appropriate platform and category (e.g., `github-actions/repo-management/`).
2. Create the `.yml` file in that directory.
3. Ensure your workflow has clear comments at the top explaining:
   - What the workflow does.
   - Any prerequisites or setup required.
   - Its Portability Rating ([D] Drop-in, [C] Configurable, or [S] Needs Setup).
4. Update the category's `README.md` to include your workflow in the index and the detailed descriptions section.
5. Open a Pull Request!

### 2. Fixing Bugs or Improving Existing Workflows
Found an issue in an existing workflow?
- Search the [Issues](https://github.com/Vishisht16/awesome-workflows/issues) to see if it has already been reported.
- If not, open a new issue using the **Bug Report** template.
- Submit a Pull Request with your proposed fix.

### 3. Requesting a Workflow
Need a workflow for a specific use case but don't know how to write it?
- Open an issue using the **Workflow Request** template. Describe the use case in detail, and the community will try to help!

---

## Pull Request Guidelines

To ensure a smooth review process, please follow these guidelines:

- **Use Conventional Commits:** We prefer PR titles that follow the [Conventional Commits](https://www.conventionalcommits.org/) specification (e.g., `feat(github-actions): add auto-tag workflow`, `fix(repo-management): correct typo in stale-issues`).
- **Update Documentation:** If your change affects how a workflow is used, make sure to update the relevant `README.md`.
- **Keep it focused:** Try to limit each PR to a single new workflow or a specific fix.
- **Check the checklists:** Ensure all items in the Pull Request Template are checked off.

## Testing Your Workflows
Before submitting, please test your workflow in a sandbox repository to ensure it behaves as expected. If the workflow requires specific configurations (like secrets), clearly document them.

Thank you for helping make Awesome Workflows better for everyone!
