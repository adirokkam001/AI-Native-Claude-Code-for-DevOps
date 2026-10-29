# Day 2 Workflow Diagram

## End-to-End Flow

```mermaid
flowchart TD
    A[Requirements prompt] --> B[Claude Code creates task tracker]
    B --> C[Unit tests and functional verification]
    C --> D{All required tests pass?}
    D -- No --> E[Inspect failure and propose fix]
    E --> C
    D -- Yes --> F[Inspect diff and .gitignore]
    F --> G[Commit and push to GitHub]
    G --> H[GitHub Actions CI workflow]
    H --> I[Push or pull request event]
    I --> J[Run automated tests]
    J --> K[Claude-assisted PR review]
    K --> L[Human checks diff, tests, and findings]
    L --> M{Ready to merge?}
    M -- No --> N[Request changes or close PR]
    M -- Yes --> O[Authorized human merges PR]
```

## Responsibility Split

| Activity | Claude Code / automation | Human |
|---|---|---|
| Generate application draft | Assists | Defines and verifies requirements |
| Run tests and diagnose failures | Assists; executes configured commands | Reviews results and edge cases |
| Create CI workflow | Generates proposed YAML | Reviews triggers, permissions, and correctness |
| Review PR | Produces findings if configured | Evaluates findings and full diff |
| Merge PR | Only if explicitly configured and authorized | Retains final approval in this learning workflow |
| Manage credentials | Uses configured secret reference | Creates, scopes, rotates, and protects credentials |
