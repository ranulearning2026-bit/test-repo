# License Compliance Summary

**Scan date:** 2026-11-24  
**Scanner:** Trivy 0.76.1 (`--scanners license --license-full`)  
**Source folder scanned:** `src/`

---

## Product License

No top-level `LICENSE*` or `LICENCE*` file was found in the repository.

`productLicense: null`

---

## Component Inventory

No bundled components were detected.

The scanner was run against `src/` and did identify Apache-2.0 SPDX licence headers inside application source files (e.g. `nova/__init__.py`, `nova/accelerator/cyborg.py`, etc.). These are **not** bundled third-party component licences — they are the project's own source-file copyright headers. Per analysis policy, only files under `vendor/`, `third_party/`, `third-party/`, or `thirdparty/` trees, or standalone `LICENSE*` / `NOTICE*` files, qualify as bundled component licence declarations. None of those exist in this repository.

**Zero bundled components detected.**

---

## Copyleft Conflicts

None — no bundled components were found.

---

## Attribution Gaps

None — no bundled components were found.

---

## Notes

- No `vendor/`, `third_party/`, `third-party/`, or `thirdparty/` directory exists anywhere in the repository.
- No standalone `LICENSE*`, `LICENCE*`, `NOTICE*` files were found at any directory depth outside of application source files.
- Trivy reported Apache-2.0 SPDX headers found in application source files only; these are excluded per analysis policy (source-file headers ≠ bundled component licences).
- If the project gains third-party dependencies in the future (e.g. a `vendor/` directory or component `LICENSE` files), re-run this analysis.
