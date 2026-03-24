---
name: Background precompute on user action
description: User wants computation to start as early as possible in background, not wait for explicit user confirmation
type: feedback
---

Start heavy computation in the background as soon as the user takes an action that implies they'll need results — don't wait for explicit confirmation.

**Why:** User complained that "computing wind fields" was still slow even after moving to Web Worker. The prefetch of weather data was early, but the actual simulation only started after user clicked Confirm. Moving the sim to start silently when mountain is selected made Confirm feel instant.

**How to apply:** When designing multi-step flows, look for opportunities to begin expensive work during earlier steps. Use a "silent run + reveal" pattern: compute in background without UI feedback, then transition to showing progress if the user catches up before completion.
