---
name: Confirmation prompts for destructive admin actions
description: Admin actions that remove data (kick, void, delete) must have a confirmation modal before executing
type: feedback
---

Any destructive admin action must show a confirmation modal with:
- Clear description of what will happen
- "Cannot be undone" warning if applicable
- Cancel + action buttons (action in danger variant)

**Why:** User explicitly requested confirmation prompt for kick player. Pattern should apply to all destructive admin actions.
**How to apply:** Use the Modal + Button components from src/ui/. State pattern: `const [confirmX, setConfirmX] = useState<...| null>(null)` where null means hidden.
