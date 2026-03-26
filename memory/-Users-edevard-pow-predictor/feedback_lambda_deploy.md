---
name: Lambda Deploy Safety
description: Each Lambda is a separate zip — never deploy wrong file to wrong function, use tennis-bot profile
type: feedback
---

Never deploy the wrong Python file to the wrong Lambda function. Each Lambda (`pow-predictor-nve-proxy`, `pow-predictor-conditions-summary`) must get its own `.py` file zipped separately.

**Why:** On 2026-03-26, `conditions_summary.py` was accidentally deployed to the NVE proxy Lambda, breaking all weather fetching in production (`Unable to import module 'nve_proxy'`).

**How to apply:** When deploying Lambda code: (1) use `tennis-bot` profile (not `pow-predictor`), (2) double-check the `--function-name` matches the file being zipped, (3) verify the Lambda works after deploy with a curl test.
