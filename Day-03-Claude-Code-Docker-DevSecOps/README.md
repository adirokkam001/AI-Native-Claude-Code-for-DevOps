# Day 3 – Claude Code with Docker and DevSecOps

## Overview
This session demonstrated how Claude Code can assist with analyzing an application repository, generating and testing a secure Docker image, scanning it with Trivy, creating Docker Compose configuration, and troubleshooting a broken container.

**Next topic:** Kubernetes (clusters, deployments, secrets, services, and security).

## Topics covered
1. Analyze an unfamiliar application repository before making changes.
2. Generate a production-oriented multi-stage Dockerfile.
3. Reduce image size and runtime attack surface.
4. Build and test the image.
5. Scan Docker configuration and images with Trivy.
6. Save an initial audit report, remediate findings, and create a follow-up report.
7. Use non-root execution, image signing with Cosign, and a local registry push test.
8. Generate a Docker Compose file with health checks, networking, resource limits, and labels.
9. Diagnose container failures with Claude Code, logs, inspection, and endpoint tests.
10. Build the same Dockerfile with Podman.

## Demonstration
The example application was **Ops Plus**, a Python Flask service with `/health` and `/info` endpoints, listening on port `8000`. The instructor reported a distroless multi-stage image size of **22.6 MB**. This is a class-demo result, not a guaranteed size for other applications.

## Notes
- [Concepts](concepts.md)
- [Practical workflow](docker-devsecops-practical.md)
- [Trivy audit and remediation](trivy-audit-and-remediation.md)
- [Docker Compose](docker-compose.md)
- [Container troubleshooting](container-troubleshooting.md)
- [Security checklist](security-checklist.md)
- [Claude prompts](prompts.md)
- [Useful commands](commands.md)
- [Workflow diagrams](diagrams/workflow.md)

## Production reminder
Claude is an assistant, not a security authority. Review generated files and commands, independently validate Trivy results, test application behavior, and require human approval before production deployment. Do not run destructive cleanup commands on production hosts.
