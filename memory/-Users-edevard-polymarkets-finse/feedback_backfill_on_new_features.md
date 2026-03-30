---
name: Backfill database on new features
description: When adding features that introduce new fields, backfill existing Firestore documents or add fallback handling so legacy data doesn't break
type: feedback
---

When a new feature adds fields to Firestore documents (e.g. `startingBalance` on rooms), always handle existing documents that lack the field. This means both:

1. **Code fallback**: `findOrCreateUser` uses `?? 200` for rooms without `startingBalance`
2. **Firestore rules fallback**: OR branch in security rules for legacy docs missing the field

**Why:** The FEST party room was created before `startingBalance` existed. The new Firestore rule did a cross-doc read expecting the field, got `null`, and blocked all new user creation for that party.

**How to apply:** Before deploying any feature that adds new fields, check if existing documents in Firestore will be affected. Add fallbacks in both application code and security rules. Consider writing a migration script to backfill existing docs if the fallback logic is complex.
