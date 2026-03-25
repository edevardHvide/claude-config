---
name: Separate AWS profiles per project
description: Don't reuse AWS profiles across projects — create dedicated IAM users with scoped permissions
type: feedback
---

Each project should have its own AWS IAM user and CLI profile with least-privilege permissions, not share a single admin profile across projects.

**Why:** User flagged that `tennis-bot` profile was being used for Pow Predictor — mixing billing, credentials, and blast radius across unrelated projects.

**How to apply:** When setting up AWS resources for a new project, create a dedicated IAM user with only the permissions that project needs. Use the admin profile only for infrastructure management (OpenTofu), not for routine deploys.
