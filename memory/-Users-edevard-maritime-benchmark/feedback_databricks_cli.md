---
name: Use Databricks CLI to run notebooks
description: Always use the Databricks CLI (not manual UI instructions) to run notebooks in this project
type: feedback
---

Use `databricks` CLI to run Databricks notebooks — don't defer to the user or give manual UI instructions when notebooks need to be executed.

**Why:** User repeatedly has to remind Claude that CLI execution is available and preferred.
**How to apply:** When notebooks need to run, use `databricks runs submit` or bundle job commands directly via the CLI that is already authenticated.
