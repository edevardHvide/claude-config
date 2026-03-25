---
name: Avoid Wasteful API Calls
description: Cache external API responses to avoid redundant fetches on reload
type: feedback
---

Cache API data locally rather than re-fetching on every page load or action.

**Why:** User finds redundant API calls wasteful — especially during development when reloading frequently.

**How to apply:** When fetching external data (NVE weather, etc.), use localStorage with a TTL. Currently weather is cached for 3 hours keyed by bbox.
