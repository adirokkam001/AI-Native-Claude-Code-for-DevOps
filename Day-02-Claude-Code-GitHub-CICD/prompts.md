# Reusable Prompts for Day 2

Use these as templates. Review the plan and changes produced by Claude Code rather than accepting them blindly.

## 1. Build the Task Tracker
> Act as a senior Python engineer. Inspect the current repository. Build a functional CLI task tracker that can add tasks, list saved tasks, and mark tasks complete. Give tasks unique IDs and persist them in JSON. Validate input, handle malformed or missing data safely, organize code into modules, add `unittest` tests, and document setup, usage, and testing in README.md. Do not include secrets or personal data. Do not run Git commands or push. Run tests, fix failures, rerun tests, and report the result.

## 2. Audit the Application
> Review the complete task tracker against its requirements. Test each feature, persistence, invalid input, and error handling. Run the existing test suite. Report what was tested, the exact commands run, failures found, fixes made, and any remaining limitations. Do not claim a test passed unless it was actually executed.

## 3. Create a Start Script
> Inspect the project and create a safe `start.sh` script that runs the documented test suite and provides a simple local demo if appropriate. Do not use destructive commands or expose secrets. Explain what the script does before I run it.

## 4. Create a GitHub Actions CI Workflow
> Inspect the repository and README. Create a GitHub Actions workflow that runs the project's tests on pushes and pull requests using a compatible Python version. Use least-privilege permissions, do not hardcode secrets, and explain the triggers and commands. Review the YAML for errors and security concerns. Do not merge or deploy.

## 5. Review a Pull Request
> Review this pull request for bugs, regressions, validation, error handling, test coverage, and security concerns. Cite the relevant files and lines. Distinguish confirmed defects from possible risks. Do not merge the PR.

## 6. Diagnose a Failed Workflow
> Inspect the failing workflow configuration and available logs. Identify the likely cause and propose the smallest safe fix. Do not reveal secrets or change permissions. Explain the fix, then wait for approval before making changes.

## 7. Prepare a PR Summary
> Summarize the purpose of this PR, key files changed, tests run and results, risks, and any follow-up work. Do not claim checks passed unless their results are available. Do not merge the PR.
