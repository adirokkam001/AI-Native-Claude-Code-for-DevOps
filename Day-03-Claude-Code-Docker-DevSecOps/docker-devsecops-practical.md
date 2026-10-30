# Practical – Analyze, Build, Scan, and Test a Docker Image

## Demonstration application
The class used **Ops Plus**, a Python Flask application with `/health` and `/info` endpoints on port `8000`.

## Phase 1: Inspect before changing files
Ask Claude Code to inspect the repository and identify:
- Language, framework, runtime, dependency files
- Entry point, startup command, listening port, endpoints
- Existing tests and test commands
- Required environment variables, secrets, writable paths, external services
- Files that should not enter the image

Ask for an analysis and plan first. Review it and approve it before allowing changes.

## Phase 2: Generate the Docker build
Ask Claude to create a multi-stage Dockerfile, suitable `.dockerignore`, minimal compatible runtime image (distroless where appropriate), non-root runtime execution, and correct startup command/port. Ask it to explain each choice.

## Phase 3: Build and test
Adjust image name, port, and endpoints to your actual project.

```bash
docker build -t ops-plus:local .
docker image ls
docker run -d --name ops-plus -p 8000:8000 ops-plus:local
docker ps
curl -i http://localhost:8000/health
curl -i http://localhost:8000/info
docker logs ops-plus
```

Do not assume another application uses port 8000 or these endpoints. Confirm from its code/configuration.

## Phase 4: Scan with Trivy

```bash
trivy --version
trivy config .
trivy image ops-plus:local
```

Check the installed version and its help for supported scanners and flags. Save raw scanner output as well as any summary.

## Phase 5: Report and remediate
The class saved an initial audit as `reports/report1.txt`, then asked Claude to review findings, make approved fixes, rebuild, retest, and create `reports/report2.txt`.

A useful report includes date/tool versions, image tag/digest, scan scope, severity counts, SBOM/secret results, findings fixed/deferred with rationale, test results, and remaining risks.

## Phase 6: Verify
Rebuild, rerun tests and endpoint checks, rescan, confirm non-root execution, check that secrets/unnecessary files are absent, and review the final report before publishing.

## Safety
Use a controlled development/test environment, least-privilege credentials, backups, and human approval. Never paste secrets into prompts or commit them to Git.
