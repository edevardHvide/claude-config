---
name: Keep Exploration as Default Landing
description: User rejected changing default landing to simulation mode — exploration mode must remain the default
type: feedback
---

Do not change the default landing mode to simulation/historical mode. The user tried this (auto-entering historicalMode=true on load, with precomputed data) and rejected it — the UX felt wrong.

**Why:** The exploration mode (click anywhere, see weather, adjust wind manually) is the intended first experience. Simulation mode requires deliberate user action (search mountain → tap Simulate).

**How to apply:** Never set `historicalMode` to `true` by default in App.tsx. The user enters simulation mode explicitly via the Simulate button or confirm dialog.
