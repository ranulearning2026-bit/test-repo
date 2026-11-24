# Infrastructure Analysis Summary

## Infrastructure Inventory

**Zero infrastructure files detected** in `src/`.

Scanned for:
- Dockerfiles (`Dockerfile`, `Dockerfile.*`, `*.dockerfile`)
- Terraform files (`*.tf`, `*.tfvars`)
- Kubernetes manifests (YAML with top-level `apiVersion` + `kind`)

None found. The repository contains only application source code (Python/Nova) and YAML test-data files; none of the YAML files carry top-level `apiVersion` fields.

## Configuration Findings

No findings — no infrastructure files to analyze.

## Secrets Detected

Gitleaks found 29 potential secrets across the repository, all in application source files (`src/nova/tests/`). Per policy, only findings in infrastructure files are reported here — **0 secrets in infrastructure files**.

## Notes

Scanners run:
| Scanner | Version | Status |
|---------|---------|--------|
| checkov | 3.4.7 | Completed — 0 infrastructure files scanned |
| trivy config | 0.76.1 | Completed — 0 config files detected |
| hadolint | 2.12.0 | Not run — no Dockerfiles found |
| gitleaks | 8.21.2 | Completed — 29 findings, all in application source (excluded) |
| conftest | 0.56.0 | Not run — no policy directory found |
