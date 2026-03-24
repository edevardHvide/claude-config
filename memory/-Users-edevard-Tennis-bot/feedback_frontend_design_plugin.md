---
name: feedback_frontend_design_plugin
description: Use the Anthropic frontend-design Claude Code plugin for UI work — user explicitly requested it
type: feedback
---

When doing UI/frontend upgrades, use the `frontend-design` Claude Code plugin (skill).

**Why:** User explicitly asked to install and use it for UI development. It's installed at `~/.claude/skills/frontend-design/SKILL.md` (from `anthropics/claude-code` repo).

**How to apply:** Invoke the `frontend-design` skill before implementing any significant UI changes. It guides bold aesthetic choices, distinctive typography, and avoids generic AI aesthetics. Pair with Playwright visual testing (see feedback_playwright_visual_testing).
