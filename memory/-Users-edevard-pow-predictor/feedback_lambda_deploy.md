---
name: Lambda Deploy Safety
description: Each Lambda is a separate zip — use correct profile per operation, verify after deploy
type: feedback
---

Never deploy the wrong Python file to the wrong Lambda function. Each Lambda (`pow-predictor-nve-proxy`, `pow-predictor-conditions-summary`, `pow-predictor-feedback`) must get its own `.py` file zipped separately.

**Profile rules:**
- `tennis-bot` — for infra changes (tofu plan/apply) and Lambda CODE deploys (`lambda:UpdateFunctionCode`)
- `pow-predictor` — for S3/CloudFront deploys AND Lambda CONFIGURATION updates (`lambda:UpdateFunctionConfiguration`, `lambda:GetFunctionConfiguration`)

**Why:** User corrected on 2026-03-26: when updating Lambda env vars (e.g. GITHUB_TOKEN), use `pow-predictor` profile — it has the necessary config permissions. Only code deploys need `tennis-bot`.

**How to apply:** (1) Match profile to operation type, (2) double-check `--function-name` matches the file being deployed, (3) verify Lambda works after any change.
