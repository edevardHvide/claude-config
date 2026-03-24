---
name: feedback_no_excessive_planning
description: User gets impatient with extended planning — wants fast execution, not lengthy analysis phases
type: feedback
---

Don't over-plan. Start implementing quickly after understanding the task.

**Why:** User explicitly interrupted planning multiple times ("are you planning?", "go", "continue") when Claude spent too long in plan mode reading files and launching agents before writing code.

**How to apply:** For tasks where the approach is clear from context (user provided a detailed spec), skip or minimize the planning phase. Read the necessary files, then start coding. Only use plan mode for genuinely ambiguous tasks where the user hasn't specified the approach.
