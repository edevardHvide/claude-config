# Hybrid Weather: NVE History + MET Forecast

## Architecture
The app fetches weather from two sources in parallel and splices them at the nearest 3-hour boundary to "now":

- **NVE seNorge** (history): 7 days back to ~now. Good for temperature and precipitation (observation-based). Wind is underestimated but less critical for historical snow that has already settled.
- **MET Locationforecast** (forecast): Today forward, ~5 days. MEPS NWP model provides realistic summit wind (6-14 m/s vs NVE's 0.5-3.7 m/s).

## Implementation
- Both APIs use 9-station 3x3 grid pattern (same as before)
- NVE requires Vite dev proxy (CORS blocked); MET has open CORS
- Splice point: find nearest 3h boundary to current time, NVE data before, MET data after
- MET hourly data for first ~2.5 days, then 6-hourly — resampled to match 3h intervals

## Wind Input Selection
Changed from domain-average wind to top-1/3 highest-altitude stations for wind solver input. High-altitude stations better represent the free-atmosphere wind that the solver then modifies with Sx terrain sheltering.
