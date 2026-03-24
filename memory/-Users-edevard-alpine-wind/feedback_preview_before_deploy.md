---
name: Preview locally before deploying
description: User wants to see changes on localhost before deploying to AWS
type: feedback
---

When making UI changes, show locally first before deploying. User said "show me locally first" when I tried to deploy immediately after building.

**Why:** User wants visual confirmation that changes look right before pushing to production CloudFront.

**How to apply:** After making UI changes, start dev server and tell the user the URL. Only deploy when they explicitly say "go" or "deploy". Don't auto-deploy after builds.
