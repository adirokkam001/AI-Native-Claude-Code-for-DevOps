# GitHub Setup for Claude Code

## Objective
Connect the project to GitHub and prepare the repository for automated CI and Claude-assisted PR review.

## 1. Create a Repository
1. Sign in to GitHub.
2. Create a new repository for the task tracker.
3. Choose public or private intentionally; a public repository exposes its source code to everyone.
4. Do not upload API keys, tokens, passwords, or local secret files.

## 2. Check Git and GitHub CLI
Run these commands in the development environment where the project is stored:

```bash
git --version
gh --version
git status
git remote -v
```

If `gh` is unavailable, install the GitHub CLI using the official installation instructions for your operating system.

## 3. Authenticate with GitHub CLI
The class demonstrated browser-based authentication with:

```bash
gh auth login
gh auth status
```

Follow the interactive prompts and verify the account and authentication method. Do not paste access tokens into chat, source files, or terminal commands that may be saved in shell history.

## 4. Commit and Push
First inspect the repository status and `.gitignore`. Then use the repository's intended branch and remote:

```bash
git status
git add .
git diff --cached
git commit -m "Add Python task tracker"
git push -u origin main
```

If your default branch is not `main`, use the actual branch name. If a remote already contains commits, inspect the history and reconcile changes carefully rather than force-pushing.

## 5. Install/Configure the Claude GitHub Integration
The class demonstrated installing the Claude GitHub App/integration for a repository. Exact menus and authentication options may change over time.

1. Open the official Claude Code GitHub integration instructions.
2. Select only the repository that needs access, where possible.
3. Review the permissions requested by the app.
4. Follow the setup flow to create the required workflow and authentication configuration.
5. Confirm the workflow file is in `.github/workflows/` and inspect it before merging.

## 6. Store Credentials as Repository Secrets
If the workflow requires an Anthropic API key, add it through the repository's **Settings → Secrets and variables → Actions** area, using the exact secret name expected by the workflow.

- Never put the key in Python code, a workflow YAML literal, README, commit, or PR comment.
- Do not share screenshots that reveal a key.
- Use the least-privileged credential and appropriate expiry/rotation.
- If a key is exposed, revoke it and create a replacement.

The class discussed a Claude subscription-linked setup and an API-key-based setup. The available authentication methods depend on the current product and workflow version; follow the official documentation for your account rather than assuming all methods are interchangeable.

## 7. Workflow Permissions
Repository settings may include workflow permissions such as read-only or read/write access. Grant only the minimum permissions required by the workflow. Do not enable broad write permissions just to make a demo succeed.

## Official References
- GitHub CLI: https://cli.github.com/
- GitHub Actions secrets: https://docs.github.com/actions/security-guides/using-secrets-in-github-actions
- Claude Code GitHub Actions: https://docs.anthropic.com/en/docs/claude-code/github-actions
