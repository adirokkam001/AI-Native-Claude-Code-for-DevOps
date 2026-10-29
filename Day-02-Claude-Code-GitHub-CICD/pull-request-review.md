# Claude-Assisted Pull Request Review

## Objective
Use Claude's GitHub integration to assist with reviewing code changes while keeping merge decisions under human control.

## Workflow
1. Create a feature branch.
2. Make a small, reviewable change.
3. Run tests locally.
4. Push the branch.
5. Open a PR against the default branch.
6. Wait for configured GitHub Actions checks.
7. Review Claude's automated comments or ask `@claude` to review, if the workflow supports that trigger.
8. Inspect the complete diff and test results yourself.
9. Request changes or approve the PR.
10. A human merges only after the repository's policies and required checks are satisfied.

## Example PR Review Comment
```text
@claude review this pull request for correctness, potential bugs,
input validation, error handling, test coverage, and security issues.
Please explain findings with file/line references. Do not merge the PR.
```

The exact comment syntax and triggers depend on the workflow configuration.

## What Claude Can Help Review
- Possible logic errors and regressions.
- Input validation and error handling.
- Missing or weak tests.
- Changes that conflict with project guidance in `CLAUDE.md`.
- Potential security issues that need human investigation.
- Whether the PR description clearly summarizes the change.

AI review is not a substitute for a security audit, code-owner review, or testing in the target environment.

## Human Approval and Merge Control
The instructor demonstrated that a request such as `@claude merge this PR` may not work if the configured workflow has no merge action or does not grant the necessary permissions. The intended safety pattern is to leave merge authority with a human.

Recommended controls:
- Protect the default branch.
- Require status checks and human reviews as appropriate.
- Do not grant the Claude workflow merge permissions unless there is an explicit, reviewed organizational need.
- Never rely on a prompt alone as the security control; enforce permissions in GitHub settings and workflow configuration.
- Review the actual workflow to confirm it cannot merge unexpectedly.

## Example Review Checklist
- [ ] The PR has a clear purpose and description.
- [ ] The diff contains only expected changes.
- [ ] Tests pass.
- [ ] No secrets or unrelated files are included.
- [ ] Claude's findings have been evaluated, not blindly accepted.
- [ ] Required human review is complete.
- [ ] The merge action is performed by an authorized human under repository policy.
