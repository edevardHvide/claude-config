---
name: Firebase project and party code
description: Firebase project ID is polymarkets-finse, party code FEST is seeded in rooms collection
type: project
---

- Firebase project: `polymarkets-finse`
- Hosting URL: https://polymarkets-finse.web.app
- Party code: `FEST` (seeded in `rooms/FEST` document with `active: true`)
- Admin code: `FINSE2026` (in `.env.local` as `VITE_ADMIN_CODE`)
- Firestore rules block `rooms/` writes — seeding requires temporary rule change + redeploy

**Why:** Needed for testing and deployment. Party code gates app entry.

**How to apply:** Use `FEST` when testing the app. If new rooms are needed, use the temporary-rule-open workflow from this session.
