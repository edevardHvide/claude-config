---
name: Mobile Testing Workflow
description: User tests mobile UX on real iPhone via local dev server
type: feedback
---

User tests on a real iPhone using `npm run dev -- --host` over local WiFi.

**Why:** Mobile bugs (touch events, layout, animations) only surface on real devices.

**How to apply:** When fixing mobile issues, suggest `--host` for testing. Mobile screenshots from user are iPhone — consider safe area insets and touch targets.
