---
name: Worktree workflow preference
description: User prefers git worktrees for feature work with merge→deploy→learn→compact sequence
type: feedback
---

User prefers creating git worktrees for feature branches rather than working directly on main.

**Why:** Keeps main clean and allows isolated development. User explicitly requested "use a working tree for this" when starting feature work.

**How to apply:** When starting new feature work, proactively suggest or use worktrees. After implementation, the user's typical sequence is: merge to main → /deploy → /learn → /compact.
