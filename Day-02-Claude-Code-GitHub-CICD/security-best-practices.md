# Security Best Practices

## 1. Protect Secrets
- Store API keys and tokens in GitHub Actions secrets or an approved secret manager.
- Never commit credentials to Git.
- Do not ask Claude to print, inspect, or reveal secret values.
- Use short-lived or narrowly scoped credentials where available.
- Revoke and rotate any credential that may have been exposed.

## 2. Use Least Privilege
- Give GitHub Apps and workflows access only to repositories and permissions they need.
- Prefer read-only permissions for review workflows when possible.
- Add write permissions only for a documented requirement.
- Avoid giving an AI workflow permission to merge or change repository settings by default.

## 3. Keep Humans in Control
- Review generated code, shell scripts, and workflow YAML.
- Inspect `git diff` before committing.
- Keep branch protection and required checks enabled.
- Treat AI review comments as suggestions that need evaluation.

## 4. Avoid Unsafe Commands
- Understand shell commands before allowing them to run.
- Be especially careful with deletion, force-push, permission changes, and production operations.
- Do not disable security controls merely to get a demonstration working.

## 5. Repository Hygiene
- Maintain a useful `.gitignore`.
- Keep documentation accurate.
- Do not commit virtual environments, caches, generated secrets, or local credentials.
- Check staged files before committing:

```bash
git status
git diff --cached
```

## 6. API Usage and Cost
The session discussed token-based usage and plan limits. Exact quotas, pricing, included usage, and authentication methods can change by product and plan. Check current official account/pricing information before estimating costs. Avoid assuming that a plan always includes a fixed token allowance.
