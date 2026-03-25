---
name: PWA safe areas must use margin not padding on fixed-size elements
description: safe-area-top as padding distorts buttons/circles — use margin-top instead
type: feedback
---

When adding `safe-area-inset-top` to position UI elements below the Dynamic Island in standalone PWA mode, use `margin-top` (or a wrapper spacer div) on fixed-size elements like buttons and circles. Using `padding-top` distorts their shape — a round compass button becomes a tall rectangle.

**Why:** MapCompass had `safe-area-top` class (padding-top) applied directly to the button element, creating a visible blank rectangle in the upper right corner on iPhone.

**How to apply:** Use `mt-[env(safe-area-inset-top)]` for positioned elements. For flex containers like the sidebar drawer, a `<div className="safe-area-top" />` spacer child is cleaner than padding on the container.
