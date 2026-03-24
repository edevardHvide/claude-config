---
name: Double-buffer Cesium imagery layers
description: Never remove old imagery layer before new one is ready — causes visible blink
type: feedback
---

When updating Cesium imagery overlays (snow, etc.), always add the new layer BEFORE removing the old one. The async `SingleTileImageryProvider.fromUrl()` creates a gap between remove and add, causing a visible flash/blink.

**Why:** User reported simulation playback was "just blinking" — each frame change showed bare terrain momentarily.

**How to apply:** Use the `SnowOverlayManager` class pattern: keep old layer visible, create new layer, crossfade, then remove old. Never call `removeSnowOverlay` before the replacement is ready.
