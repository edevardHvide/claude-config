---
name: Commit before deploy
description: Always commit changes before deploying to Firebase
type: feedback
---

When the user says "deploy", always commit first, then build and deploy.

**Why:** User wants a clean git state before each deploy so deployments are traceable to commits.

**How to apply:** On any "deploy" request, run git add + commit for pending changes before npm run build + firebase deploy.
