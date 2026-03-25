---
name: Use relative coloring for snow redistribution
description: Absolute depth color scale saturates — use deviation from mean to show wind redistribution
type: feedback
---

Historical snow overlay must color by **deviation from domain mean**, not absolute depth. With 12 days of accumulation, total depth easily exceeds 60cm everywhere. An absolute color scale (0-60cm) saturates and shows uniform color even when wind has redistributed 20+ cm between ridges and lee slopes.

**Why:** User reported "snow looks homogenous in the simulation" despite 10 m/s wind at Store Ringstind. All cells were 65-90cm depth, all mapping to the same saturated dark blue because the color scale capped at 60cm.

**How to apply:** `historicalSnowColor(depthCm, meanCm, spreadCm)` takes domain mean and max deviation. The overlay computes these per frame. Brown = scoured (below avg), neutral = average, blue = loaded (above avg). Alpha still scales with absolute depth so early timesteps with little snow stay faint.
