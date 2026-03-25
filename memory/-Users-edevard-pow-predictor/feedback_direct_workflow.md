---
name: Direct workflow commands
description: User gives chained commands like "pull, push, deploy" — execute without asking, commit implicitly if needed
type: feedback
---

When user gives chained action commands (e.g., "pull from main, then push, then /deploy"), just execute them sequentially. If uncommitted changes exist and push is requested, commit them with an appropriate message without asking first.

**Why:** User prefers action over confirmation dialogs for routine operations.
**How to apply:** For standard git+deploy workflows, be proactive. Only pause for genuinely destructive or ambiguous actions.
