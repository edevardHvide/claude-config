---
name: Keep repo clean
description: User dislikes clutter — remove unused files/configs, keep git status clean
type: feedback
---

User expects a clean repo. When unused files accumulate (e.g., plugin bloat, test artifacts), proactively suggest or perform cleanup. Add generated/ephemeral directories to .gitignore.

**Why:** User noticed 30+ unused .claude skill directories polluting git status and wanted them removed immediately.
**How to apply:** After installing tools or plugins, check what got added and remove anything not project-specific. Keep .gitignore current.
