# Claude Code Prompt Examples – Day 3

Run prompts from the application repository. Review plans before approving file changes or commands.

## 1. Repository analysis (read-only first)

```text
Inspect this application repository without changing files. Identify
language, framework, runtime, dependency files, entry point, startup
command, listening port, health/info endpoints, tests, required
environment variables, writable paths, and external services. Identify
files that must not be copied into a container. Do not print secret
values. Return an architecture summary, risks, unknowns, and a proposed
Dockerization plan. Wait for my approval.
```

## 2. Multi-stage Dockerfile

```text
Based on the approved analysis, propose a secure multi-stage Dockerfile.
Use a minimal compatible runtime image, copy only runtime artifacts,
run as a non-root user, and use the verified startup command and port.
Create or update .dockerignore. Explain trade-offs and compatibility.
Do not claim production readiness until build, tests, and scans pass.
Show the plan and wait for approval before editing.
```

## 3. Build and test

```text
Build the image with a clear local tag. Run it in a controlled local
environment. Test documented health/info endpoints, inspect logs, and
report build/test results. Do not remove unrelated images, containers,
volumes, or files.
```

## 4. Trivy audit

```text
Run Trivy configuration and final-image scans using scanners supported
by the installed version. Save raw output under reports/. Summarize
findings by severity, affected packages, and available fixes. Distinguish
builder-stage findings from final runtime findings where possible.
Do not suppress findings. Wait for approval before remediation.
```

## 5. Remediation and report

```text
Review raw Trivy output and the initial report. Propose minimal fixes,
explain breaking-change risks, and wait for approval. After approval,
make changes, rebuild, rerun application tests and scans, and save a
post-remediation report. Include unresolved findings and rationale.
Do not claim the image is secure solely because a scan reports no findings.
```

## 6. Compose file

```text
Create a Compose configuration using the verified image/build context
and correct port. Include an appropriate health check, dedicated
network, restart policy, labels, and resource limits where supported.
Consider non-root execution, read-only filesystem, and dropped
capabilities where compatible. Validate the configuration and explain
environment-specific settings. Wait for approval before starting services.
```

## 7. Incident troubleshooting

```text
Investigate the named container without deleting resources. Inspect its
state, logs, health check, port mapping, application bind address,
startup command, and relevant Docker/Compose configuration. Test the
expected endpoint. Identify root cause and propose the smallest safe fix.
Back up files and wait for approval before editing. After approval,
rebuild and retest, then report exact changes and remaining risks.
```
