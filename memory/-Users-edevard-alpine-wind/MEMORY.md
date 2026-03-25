# Memory Index

- [feedback_worktree_workflow.md](feedback_worktree_workflow.md) — User prefers worktree-based feature development with merge→deploy→learn sequence
- [feedback_background_precompute.md](feedback_background_precompute.md) — Start heavy computation in background immediately on user action, don't wait for confirmation
- [feedback_mobile_overflow_hidden.md](feedback_mobile_overflow_hidden.md) — overflow-hidden clips absolutely-positioned dropdowns on mobile
- [feedback_preview_before_deploy.md](feedback_preview_before_deploy.md) — Show changes on localhost before deploying to AWS
- [feedback_cesium_double_buffer.md](feedback_cesium_double_buffer.md) — Never remove old Cesium imagery layer before new one is ready (causes blink)
- [feedback_percell_temp_check.md](feedback_percell_temp_check.md) — Per-cell snowfall arrays must bypass global temperature early return
- [feedback_playwright_dynamic_import.md](feedback_playwright_dynamic_import.md) — Use page.evaluate + dynamic import for Playwright tests (CesiumJS fails headless)
- [feedback_nve_wind_underestimate.md](feedback_nve_wind_underestimate.md) — NVE seNorge grid underestimates summit wind (0.5-3.7 m/s vs real 6-14 m/s); observation-interpolated bias
- [feedback_relative_snow_coloring.md](feedback_relative_snow_coloring.md) — Color snow by deviation from mean, not absolute depth (avoids saturation)
- [feedback_pwa_safe_areas.md](feedback_pwa_safe_areas.md) — Use margin not padding for safe areas on fixed-size elements (buttons distort)
- [feedback_svg_not_emoji_icons.md](feedback_svg_not_emoji_icons.md) — Use SVG icons not emoji for UI controls (inconsistent rendering)
- [feedback_separate_aws_profiles.md](feedback_separate_aws_profiles.md) — Separate AWS IAM users per project, don't share profiles
- [project_aws_deployment.md](project_aws_deployment.md) — AWS infra managed by OpenTofu with separate deploy/admin profiles
- [project_hybrid_weather.md](project_hybrid_weather.md) — Hybrid weather: NVE for history (7d back), MET for forecast (today forward), spliced at 3h boundary
- [project_snow_overlay_smoothing.md](project_snow_overlay_smoothing.md) — 4x canvas upscale with bilinear smoothing eliminates blocky snow overlay
- [project_snow_particles.md](project_snow_particles.md) — White/blue snow-like particles (10K desktop/4K mobile) replaced colored streamlines
- [reference_ruflo.md](reference_ruflo.md) — Ruflo (claude-flow) is the MCP orchestration platform, not a frontend library
- [reference_met_api.md](reference_met_api.md) — MET Norway Locationforecast 2.0 API: open CORS, User-Agent header, MEPS NWP wind data
