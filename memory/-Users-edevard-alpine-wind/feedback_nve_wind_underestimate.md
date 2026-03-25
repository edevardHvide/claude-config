# NVE seNorge Grid Underestimates Summit Wind

## Discovery
NVE GridTimeSeries API was returning 0.5-3.7 m/s wind at mountain summits while yr.no (MET Norway) showed 6-14 m/s for the same locations. This caused unrealistically low snow redistribution in the simulation.

## Root Cause
NVE seNorge is an observation-interpolated 1km grid. Norwegian weather stations are predominantly in valleys and sheltered locations, so the interpolated grid systematically underestimates wind at exposed summits and ridges.

## Solution
Switched to hybrid approach: NVE for historical data (good for temperature and precipitation), MET Locationforecast for forecast period (good for wind). See `project_hybrid_weather.md`.

## Lesson
When simulation output looks unrealistically uniform or weak, check input data quality against independent sources (e.g., yr.no for weather). The model physics may be correct but starved of realistic inputs.
