---
name: feedback_playwright_visual_testing
description: User wants Playwright visual testing for UI changes — test rendering at each step
type: feedback
---

Use Playwright (headed browser) to verify UI/rendering changes actually work visually.

**Why:** User explicitly requested "test with playwright every step that it renders" for the physics overhaul. Visual simulation changes can't be verified by type-checking alone.

**How to apply:** For changes that affect visual output (snow overlays, map rendering, UI components), write a quick Playwright script that loads the app, interacts with controls, captures console logs and screenshots, then checks for errors. Clean up test files after verification. The alpine-wind project has Playwright installed as a dev dependency.
