# Container Troubleshooting with Claude Code

## Class scenario
The instructor intentionally introduced Dockerfile mistakes, including an incorrect Python executable reference and wrong port value. The container could appear to be running or healthy while the application endpoint was not reachable as expected.

Claude Code was asked to inspect the container, identify the incorrect configuration, make a correction, rebuild, and test again. The instructor reported correcting a Dockerfile line and restoring the application port to `8000`; line numbers depend on the file version.

## Diagnostic commands

```bash
docker ps
docker ps -a
docker logs <container-name>
docker inspect <container-name>
docker port <container-name>
docker compose ps
docker compose logs
```

Test from the host using the actual mapped port:

```bash
curl -i http://localhost:8000/health
```

## Ask Claude to investigate
Ask it to inspect container state, logs, health check, port mapping, application bind address, startup command, and relevant Docker/Compose files. Ask it to identify the root cause before changing files. Require a backup, minimal fix, approval, rebuild, endpoint test, and a report of changes.

## Key checks
- Is the application process running?
- Is it listening on `0.0.0.0` inside the container rather than only `127.0.0.1`?
- Do application, container, and host ports match?
- Is the startup command valid?
- Are dependencies installed?
- Is the health-check command compatible with the image?
- Are environment variables and permissions correct?

A container's `healthy` status means its configured health check passed. It does not prove every endpoint or external route works.
