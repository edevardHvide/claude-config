---
name: Use page.evaluate + dynamic import for Playwright module tests
description: CesiumJS fails in headless Chromium — test modules directly via dynamic import in browser context
type: feedback
---

CesiumJS requires WebGL which fails in headless Chromium. UI-driven tests (clicking search, waiting for terrain) don't work. Instead, test simulation/API modules directly using `page.evaluate` with dynamic `import()`:

```js
const result = await page.evaluate(async () => {
  const mod = await import("/src/api/nve.ts");
  return mod.fetchSpatialWeather(...);
});
```

**Why:** Playwright tests that tried to interact with the UI (search mountains, click map) got zero API requests and zero console logs because CesiumJS crashed before any UI rendered.

**How to apply:** For testing non-UI code paths (API fetch, simulation logic), use direct module imports in `page.evaluate`. Reserve UI tests for non-CesiumJS components only.
