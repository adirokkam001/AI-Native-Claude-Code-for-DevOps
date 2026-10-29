# GitHub Actions – Continuous Integration

## Objective
Use GitHub Actions to run automated validation when code is pushed or a pull request is opened or updated.

## What the Class Demonstrated
Claude Code was asked to inspect the task tracker repository and create a GitHub Actions workflow. The intended CI workflow runs the application's tests on relevant GitHub events. The instructor deferred detailed YAML explanation to later CI/CD or Jenkins classes.

## Typical CI Sequence

1. A developer pushes a commit or opens/updates a PR.
2. GitHub Actions detects an event configured in the workflow.
3. A runner checks out the repository.
4. The runner sets up the required Python version.
5. Dependencies are installed, if any.
6. Unit tests run.
7. GitHub reports pass/fail status checks.
8. Reviewers use those results when deciding whether the PR is ready.

## Workflow Location
GitHub Actions workflow files normally live in:

```text
.github/
└── workflows/
    └── ci.yml
```

The actual filename can differ. Inspect the repository to find the workflow Claude generated.

## Prompt to Generate a CI Workflow
> Inspect this repository and its README. Create a GitHub Actions CI workflow that uses a suitable supported Python version, installs required dependencies if any, and runs the project's unit tests on pushes and pull requests. Use least-privilege permissions. Do not add secrets to the workflow file. Explain the triggers and commands used. After creating the workflow, review it for correctness and security. Do not merge or deploy anything.

## Review Before Enabling
- Does the workflow run the correct test command?
- Is the Python version compatible with the project?
- Are dependency installation steps correct?
- Are triggers limited to the intended branches/events?
- Are permissions no broader than necessary?
- Are third-party actions pinned or otherwise managed according to your organization's policy?
- Are secrets referenced by name and stored in GitHub Secrets?
- Does the workflow avoid exposing secrets in logs?
- Do required status checks match the repository's branch protection policy?

## CI Is Not the Same as Deployment
A test workflow is CI. Do not assume the application is automatically deployed just because tests run. Deployment stages, environments, approvals, and rollback policies must be designed separately.

## Important
Treat generated YAML as code. Read the complete workflow and understand its permissions and actions before enabling it in a real repository.
