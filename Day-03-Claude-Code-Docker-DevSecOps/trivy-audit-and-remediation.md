# Trivy Audit and Remediation

## Purpose
Trivy was used to scan Docker configuration and the built image, identify findings, and support a remediation-and-rescan cycle.

## Suggested workflow
1. Record image name/tag and build context.
2. Run a configuration scan.
3. Run an image vulnerability scan.
4. Generate/review an SBOM where required.
5. Run secret scanning where appropriate.
6. Save raw output in a reports directory.
7. Ask Claude to explain findings and propose fixes.
8. Review and approve changes.
9. Rebuild, retest, and rescan.
10. Save a post-remediation report.

## Example commands

```bash
mkdir -p reports
trivy config .
trivy image ops-plus:local
trivy image --format json --output reports/trivy-image.json ops-plus:local
```

Exact flags and scanners depend on the installed Trivy version. Check `trivy --help` and documentation for that version.

## Report naming
The class used `reports/report1.txt` for the initial audit and `reports/report2.txt` for the post-remediation report. Consider timestamped reports and retain raw scanner output.

## Review carefully
- Triage findings; not every issue has an available fix.
- Distinguish build-stage packages from packages in the final runtime image where possible.
- Record exceptions with an owner, rationale, and review date.
- Do not claim “zero vulnerabilities” unless supported by the actual scan output and scope.
- Verify AI-generated summaries against raw Trivy output.
