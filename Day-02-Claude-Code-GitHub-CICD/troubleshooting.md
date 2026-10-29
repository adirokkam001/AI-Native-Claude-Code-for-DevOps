# Troubleshooting – Claude Code, GitHub, and CI

## 1. `gh: command not found`
**Likely cause:** GitHub CLI is not installed or is not on `PATH`.

**Check:**
```bash
gh --version
```
Install GitHub CLI using the official instructions for your operating system, then reopen the terminal if needed.

## 2. Git Push Is Denied
**Possible causes:** Wrong GitHub account, expired/missing authentication, wrong remote URL, or insufficient repository permission.

**Check:**
```bash
git remote -v
git status
gh auth status
```
Confirm the account has write access. Do not paste credentials into source code or chat.

## 3. GitHub Actions Does Not Run
- Confirm the workflow is under `.github/workflows/`.
- Check whether the event and branch match the workflow's `on` configuration.
- Open the repository's Actions tab and inspect the run logs.
- Check whether Actions are enabled and whether repository/organization policy blocks the workflow.

## 4. Tests Fail in CI but Pass Locally
- Compare Python versions.
- Check dependency installation and lock/version files.
- Look for assumptions about local files, environment variables, or working directories.
- Reproduce the exact CI test command locally when possible.

## 5. Claude Does Not Respond to `@claude`
- Verify the Claude GitHub App/integration is installed for the repository.
- Check that the relevant workflow exists and is enabled.
- Confirm the comment event is included in workflow triggers.
- Check workflow run logs and repository permissions.
- Verify the required secret name exists without exposing its value.

## 6. Claude Cannot Merge a PR
This may be intentional. A workflow cannot perform an action that its code, token permissions, or repository rules do not allow. In this course's intended safety model, a human performs the final merge.

## 7. Authentication or API Key Error
- Verify the expected authentication method for the installed integration.
- Confirm the secret name matches the workflow reference.
- Rotate a key if it may have been exposed.
- Never print the secret value to debug the problem.

## 8. Use Claude for Diagnosis Safely
Example prompt:

> Inspect the failing GitHub Actions run configuration and relevant test logs. Identify the likely cause and propose the smallest fix. Do not reveal secrets, modify repository permissions, push changes, merge a PR, or deploy anything. Explain the proposed change before applying it.

Always inspect proposed changes and rerun the checks after a fix.
