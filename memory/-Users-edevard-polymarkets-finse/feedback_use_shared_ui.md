---
name: Use shared UI primitives
description: Always use Button/Modal/Input/Card from src/ui/ instead of inline Tailwind classes
type: feedback
---

Use the shared components from `src/ui/` for all new UI work:
- `Button` — variant: primary/danger/success/secondary, size: sm/md/lg, fullWidth prop
- `Modal` — onClose callback, className for panel overrides
- `Input` — forwardRef, all native input props
- `Card` — className for overrides

**Why:** Session refactoring (Phase 4) extracted these from 9 files of duplicated Tailwind. Going back to inline classes defeats the purpose.
**How to apply:** Import from `../../ui` (or appropriate relative path). Never copy-paste modal/button/input/card Tailwind classes inline.
