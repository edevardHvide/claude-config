---
name: Enforce limits in three places
description: Validation limits (max bet, max odds) must be enforced in HTML input, form validation, AND server-side service
type: feedback
---

When adding a limit (e.g. max bet 100kr, max odds 100:1), enforce it in all three layers:
1. HTML input constraint (`max={100}`)
2. Client-side form validation with user-friendly error message
3. Server-side in the service function (throw before transaction)

**Why:** User set max bet to 100 and max odds to 100 — both needed all three layers for proper enforcement.
**How to apply:** Any time a numeric limit is introduced, check all three validation points exist.
