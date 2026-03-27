---
name: AWS Profile Rules
description: Use pow-predictor profile for ALL AWS operations in this project — no other profile
type: feedback
---

**Use `pow-predictor` profile for ALL AWS operations** — Lambda deploys, S3, CloudFront, logs, config, everything.

**Why:** User has corrected this multiple times. There is only one profile for this project.

**How to apply:** Always use `--profile pow-predictor` for any AWS CLI command in this project.
