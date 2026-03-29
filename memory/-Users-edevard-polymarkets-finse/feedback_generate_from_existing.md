---
name: Generate artifacts from existing files
description: User prefers generating planning artifacts from existing docs rather than interactive questioning
type: feedback
---

When a planning artifact (like CONTEXT.md) is missing, offer to generate it from existing planning files (ROADMAP.md, REQUIREMENTS.md, STATE.md, codebase) rather than requiring an interactive discuss-phase session.

**Why:** User said "use the other md files to generate this" when CONTEXT.md was missing, skipping the interactive discuss-phase workflow.

**How to apply:** If discuss-phase hasn't been run and CONTEXT.md is needed, offer generation from existing artifacts as the first option. Only suggest interactive discuss-phase if the user wants to add design preferences not captured elsewhere.
