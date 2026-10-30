# Docker Security Checklist

## Before building
- [ ] Understand application, entry point, dependencies, ports, and endpoints.
- [ ] Identify secrets and exclude credentials and `.env` files from build context.
- [ ] Review base image, version, provenance, and maintenance status.
- [ ] Use multi-stage build where appropriate.
- [ ] Keep runtime image minimal.

## Runtime
- [ ] Run as non-root where supported.
- [ ] Copy only required runtime files.
- [ ] Do not embed secrets in image layers or build arguments.
- [ ] Use appropriate environment/secret management.
- [ ] Restrict Linux capabilities where compatible.
- [ ] Use read-only filesystem where supported.
- [ ] Set suitable resource limits and health checks.

## Scan and verify
- [ ] Scan Docker configuration with Trivy.
- [ ] Scan final image with Trivy.
- [ ] Generate/review SBOM where required.
- [ ] Review secret-scan results.
- [ ] Rebuild and rescan after remediation.
- [ ] Test application endpoints and startup.
- [ ] Verify runtime user and image contents.
- [ ] Retain raw scan output and review reports.

## Supply chain and approval
- [ ] Sign images where required (the class demonstrated Cosign).
- [ ] Verify signatures before deployment.
- [ ] Use immutable tags/digests for release traceability.
- [ ] Review Claude's plan and generated files.
- [ ] Independently validate scanner results.
- [ ] Require human approval before production.
