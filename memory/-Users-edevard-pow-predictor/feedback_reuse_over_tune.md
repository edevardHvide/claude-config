---
name: Reuse Working Logic Over Parameter Tuning
description: When a working system exists (e.g. historical sim), reuse it rather than tuning parameters on the simpler version
type: feedback
---

When a more sophisticated version of something already works well (e.g., historical simulation mode), reuse that logic for the simpler mode rather than spending time tuning raw physics parameters. User explicitly said "just use the simulation logic, it works fine. reuse! set to some precipitation amount that gives a good animation."

**Why:** Parameter tuning with test harnesses is slow and uncertain. The historical sim already produces good-looking results because it accumulates over multiple time steps — just feed it fixed inputs.

**How to apply:** When exploration/manual mode needs improvement, adapt the proven historical sim approach (multi-step accumulation, compound redistribution) rather than tweaking erosion rates, sublimation coefficients, etc. in isolation. Favor reusing battle-tested code paths.
