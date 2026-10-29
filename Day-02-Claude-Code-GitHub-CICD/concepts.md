# Core Concepts – Claude Code for DevOps

## 1. Code Generation vs. Agentic Workflow

**Code generation** means asking an AI model to produce code or a configuration file.

An **agentic workflow** goes further: the tool can work in a project environment, inspect files, run commands and tests, examine failures, make proposed changes, and repeat verification. Human review remains important because test results do not prove that software is secure or correct in every situation.

## 2. The Main Components

| Component | Purpose in the practical |
|---|---|
| Claude Code | Assists with project files, commands, tests, Git operations, and workflow generation |
| Python CLI task tracker | Sample application used to demonstrate the lifecycle |
| Git | Tracks local source-code history |
| GitHub repository | Hosts source code and collaboration workflow |
| Feature branch | Isolates proposed changes from the main branch |
| Pull request (PR) | Provides a review point before merging changes |
| GitHub Actions | Runs automated jobs such as tests on configured events |
| Repository secrets | Store sensitive values for workflows without hardcoding them in source |
| Human reviewer | Evaluates changes and makes the merge decision |

## 3. Typical GitHub Flow

1. Keep stable code on the default branch, commonly `main`.
2. Create a separate feature branch for a change.
3. Make and test the change.
4. Push the feature branch to GitHub.
5. Open a PR against the default branch.
6. Automated CI checks run according to the workflow configuration.
7. Claude can review the PR if the GitHub integration and workflow are configured.
8. A human reviews the diff, test results, permissions, and feedback.
9. Merge only when the repository's rules and the human reviewer allow it.

## 4. CI vs. CD

- **Continuous Integration (CI):** Automatically validates changes, often by installing dependencies and running tests on pushes and PRs.
- **Continuous Delivery/Deployment (CD):** Extends the pipeline toward packaging and releasing or deploying the application. Deployment requires additional safeguards and was not the central demonstrated task in this session.

## 5. Why Human Approval Matters

An AI review is useful assistance, not a guarantee. Tests may miss defects, and an AI may misunderstand requirements or overlook security issues. Keep protected-branch rules and required checks enabled, and require a human to make the final merge decision.

## 6. `CLAUDE.md`

A repository-level `CLAUDE.md` can document project conventions, test commands, architecture, coding rules, and review expectations. It provides context to Claude Code, but it is not a security boundary and does not replace code review or repository permissions.
