# Dependency Analysis Summary

**Repository:** `git@github.com:ranulearning2026-bit/test-repo.git`
**Branch:** `agent_workspace`
**Date:** 2026-11-24

## Manifest Inventory

No dependency manifests were found in the repository. The following manifest types were searched at all directory depths:

| Manifest Type | Ecosystem | Count Found |
|---|---|---|
| `pom.xml` | Maven (Java) | 0 |
| `requirements.txt` | pip (Python) | 0 |
| `package.json` | npm (Node.js) | 0 |
| `go.mod` | Go modules | 0 |

**Zero manifests found. No dependencies to inventory.**

## Advisory Matches

_Omitted — no dependency manifests found._

## Unpinned Dependencies

_Omitted — no dependency manifests found._

## Notes

- **Manifest scan:** Searched entire repository tree for `pom.xml`, `requirements.txt`, `package.json`, `go.mod`. None found.
- **Scanners run:**
  - trivy v0.76.1 — completed successfully; reported 0 language-specific files.
  - osv-scanner v1.9.2 — failed: target path `/src` does not exist in this environment; advisory scan for all ecosystems was not performed via osv-scanner.
- **Advisory coverage:** Trivy found no lockfiles or manifests to scan. OSV scanner could not run due to missing `/src` path. No advisory data is available for this repository. This should **not** be interpreted as "no known vulnerabilities" — it means the advisory scan could not be completed.
