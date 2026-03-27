---
name: Check API client code before testing endpoints
description: Always read existing API client code (e.g. src/api/nve.ts) before manually testing endpoints — don't guess URL formats
type: feedback
---

Always read the existing API client code before smoke-testing endpoints manually. Do not guess URL formats from memory.

**Why:** NVE API uses path-based UTM33 coordinates (`/{x}/{y}/{start}/{end}/{theme}.json`), not query-string parameters. I've incorrectly used `?x=&y=&parameterIds=` format multiple times, getting false 404/502 errors.

**How to apply:** Before any manual `curl` test of an API endpoint, read the corresponding client file (e.g. `src/api/nve.ts`) to see the exact URL format. The `fetchTheme` function at line 71 shows the correct pattern.
