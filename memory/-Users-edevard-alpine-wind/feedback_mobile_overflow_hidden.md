---
name: Mobile overflow-hidden clips dropdowns
description: overflow-hidden on mobile search bar container clips absolutely-positioned dropdown results
type: feedback
---

Do not use `overflow-hidden` on containers that have children with absolutely-positioned dropdowns/popups.

**Why:** The mobile floating search bar had `rounded-full overflow-hidden` which clipped the MountainSearch dropdown results. The input uses `bg-transparent` in mobile mode so there's nothing to clip anyway.

**How to apply:** When adding `overflow-hidden` for `rounded-*` clipping, check if any child renders absolutely-positioned content that extends beyond the container bounds.
