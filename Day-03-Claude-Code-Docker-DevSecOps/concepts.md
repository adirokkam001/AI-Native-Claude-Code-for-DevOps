# Day 3 Concepts – Claude Code with Docker

## Repository analysis
Before writing a Dockerfile, ask Claude Code to inspect the repository and report the language/framework, runtime, dependencies, entry point, startup command, listening port, endpoints, tests, environment variables, secrets, writable paths, and external services. Ask for a plan first and approve it before changes.

## Multi-stage Docker build
A multi-stage build separates build-time dependencies from the final runtime image:
- **Builder stage:** installs dependencies and prepares application artifacts.
- **Runtime stage:** copies only the files needed to run the application.

This can reduce image size and remove unnecessary tools from the runtime image. A smaller image can reduce attack surface, but does not prove an image is secure.

## Distroless images
Distroless images contain only application runtime components and dependencies. They generally omit a shell and package manager, reducing unnecessary components. Debugging may require separate debug images or external tools.

## Trivy
Trivy was used to scan Docker configuration for misconfiguration, images for known vulnerabilities, and to support SBOM and secret checks. Review actual scanner output; do not rely only on an AI-generated summary.

## Remediation cycle
1. Build the image.
2. Test the application and endpoints.
3. Scan configuration and image.
4. Save an initial report (`reports/report1.txt` in the demo).
5. Review findings and remediate.
6. Rebuild and rescan.
7. Save a follow-up report (`reports/report2.txt` in the demo).
8. Verify the final image and application manually.

A report with zero findings is not a universal guarantee of security. Results depend on scanner databases, configuration, and image contents.

## Non-root runtime and image signing
Run as a non-root user where supported. Check file ownership and writable paths. The class demonstrated Cosign for image signing; signing helps establish authenticity and integrity when verification is enforced, but does not make an image vulnerability-free.

## Docker Compose
Compose describes and runs an application. The demo included health checks, a dedicated network, CPU/memory limits, labels, and restart behavior.

## Troubleshooting
Claude can help interpret `docker ps`, `docker logs`, `docker inspect`, Compose logs, port mappings, health checks, and endpoint tests. Validate every proposed fix.

## Podman
The instructor explained that Podman can build from the same Dockerfile using `podman build` instead of `docker build`.
