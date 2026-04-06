---
name: Cache Version Busting
description: Bump localStorage cache key prefix when changing data sources to prevent stale data
type: feedback
---

When changing what data a cached result contains (e.g., adding MEPS wind to weather cache), bump the cache key prefix version (e.g., `pow-weather-` → `pow-weather-v2-`).

**Why:** User saw 1.5 m/s wind at Sudnadalen because localStorage had pre-MEPS cached weather from the old `pow-weather-` key. The 3h TTL wasn't enough — the user had recently loaded the same area.

**How to apply:** Any time the shape or source of cached data changes, bump the version in the cache key prefix. This forces all clients to re-fetch fresh data.
