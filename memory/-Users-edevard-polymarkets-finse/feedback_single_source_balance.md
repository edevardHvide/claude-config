---
name: Single source of truth for computed values
description: Derive committedStake and locked balance from one data source (openBets), not multiple store values
type: feedback
---

Compute derived values like committedStake from a single data source rather than combining multiple store values that update at different times.

**Why:** Using `pendingPickup` (single value from `find()`) alongside `openBets` caused incorrect locked balance — the store only held one pending bet, and the two listeners could update at different times causing race conditions and off-by-N errors.

**How to apply:** When calculating aggregates from realtime data, prefer reducing over one collection (e.g., `openBets.reduce(...)`) rather than stitching together values from separate store fields. If a Firestore query scope changes (e.g., adding `'pending'` to the status filter), audit all downstream computations that relied on the old scope.
