# Snow Overlay Canvas Smoothing

## Problem
Snow overlay canvas was rendering at native grid resolution (1 pixel per cell, ~280x290 pixels), producing blocky/pixelated appearance on the 3D terrain.

## Solution
Upscale canvas 4x (e.g., 280x290 -> 1120x1160) and use `ctx.imageSmoothingEnabled = true` with `ctx.imageSmoothingQuality = "high"` to get smooth bilinear interpolation between cells. The snow depth data is drawn at grid resolution first, then the upscaled canvas with smoothing produces gradual color transitions.
