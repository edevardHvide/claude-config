---
name: Deploy must commit first
description: Always commit all pending changes before running /deploy — don't deploy uncommitted work
type: feedback
---

Always commit all pending changes before deploying. The deploy skill bumps version and commits that, but any other uncommitted work must be committed first.

**Why:** User expects deploy to ship everything that's been worked on, not leave changes behind.

**How to apply:** When /deploy is invoked, check git status first. If there are uncommitted changes, commit them with a descriptive message before proceeding to version bump + build + deploy.
