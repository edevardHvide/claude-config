---
name: AWS deployment and IaC setup
description: Pow Predictor AWS infra managed by OpenTofu with separate deploy/admin profiles
type: project
---

App is deployed and live at https://d1y1xbjzzgjck0.cloudfront.net.

**Infrastructure as Code:** All AWS resources are codified in `infra/` directory using OpenTofu. State stored in `s3://pow-predictor-tfstate` (versioned).

**Two AWS profiles:**
- `tennis-bot` — admin, used for `tofu plan/apply` and infra management
- `pow-predictor` — scoped deploy user (S3 sync, CloudFront invalidation, Lambda update, CloudWatch logs only)

**Why:** User wants project infrastructure separated per project, not sharing profiles across apps.

**How to apply:** Use /deploy skill (profile `pow-predictor`) for app deployments. Use `tennis-bot` profile for infra changes via `cd infra && tofu plan/apply`.
