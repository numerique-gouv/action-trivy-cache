# action-trivy-cache

## `security-trivy-critical` action

You can add this action to your workflow to scan your codebase for critical vulnerabilities using Trivy.

```yaml
  security-trivy-critical:
    permissions:
      contents: read
      security-events: write
    runs-on: ubuntu-latest
    steps:
      - name: Run Trivy analysis for critical vulnerabilities
        uses: numerique-gouv/action-trivy-cache/security-trivy-critical@main
```

This check will scan your repository for vulnerabilities and report any critical issues
found in the Security tab of your GitHub repository.

This action will never fail the workflow, it will only report the vulnerabilities found.

You can then add the "GitHub Advanced Security / Trivy" to the required checks for your branches
in the branch protection rules to ensure that no critical vulnerabilities are introduced
in your codebase.


## `security-trivy` action

You can add this action to your workflow to scan your codebase for vulnerabilities using Trivy.

This action does not report the vulnerabilities to GitHub Security tab, but it can be used to fail the workflow
if any vulnerability is found. It's not recommended to make this check required in branch protection rules,
as it may block merges due to non-critical vulnerabilities.

```yaml
  security-trivy:
    permissions:
      contents: read
    runs-on: ubuntu-latest
    steps:
      - name: Run Trivy analysis for vulnerabilities
        uses: numerique-gouv/action-trivy-cache/security-trivy@main
```
