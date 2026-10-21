# CI Smoke Check

This repository verifies that GitHub Actions is working end to end.

## Smoke test

The workflow at `.github/workflows/smoke.yml` is manually triggerable (`workflow_dispatch`) and runs a trivial check on `ubuntu-latest`.

- Run ID: 39669912300
- Conclusion: success
- Workflow: Smoke Check
- Log excerpt: `Smoke check started` → `2 + 2 = 4` → `Smoke check completed successfully`
