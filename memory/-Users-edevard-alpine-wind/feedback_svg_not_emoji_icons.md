---
name: Use SVG icons not emoji for UI controls
description: Emoji characters render inconsistently across platforms — use inline SVG for playback controls
type: feedback
---

Never use emoji characters (⏸, ▶, ◀) for UI controls. They render differently on iOS, Android, and desktop — different sizes, colors, and sometimes as colored emoji instead of monochrome symbols.

**Why:** Pause button (⏸) looked unprofessional on iPhone PWA — rendered as a colored emoji glyph instead of a clean icon.

**How to apply:** Use inline SVG with explicit fill colors. Keep viewBox consistent (e.g., `viewBox="0 0 24 24"`) and size via width/height attributes.
