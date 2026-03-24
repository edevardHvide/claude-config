---
name: Per-cell snowfall bypasses global temperature check
description: When snow model receives Float64Array snowfall, skip the params.temperature > 1 early return
type: feedback
---

The global `params.temperature > 1` early return in `computeSnowAccumulation` must be bypassed when passing per-cell snowfall arrays. The per-cell array already has temperature filtering baked in (cells with temp > 0 have snowfall = 0).

**Why:** The domain-average temperature can be above freezing while high-altitude cells are below freezing. The global check kills all snow redistribution even when some cells should receive snow. This was a bug that made spatial weather appear to have "only one data point."

**How to apply:** The check now reads `typeof snowfallCm === "number" && params.temperature > 1`. Only applies to uniform scalar snowfall (manual mode), not per-cell arrays (historical mode with spatial weather).
