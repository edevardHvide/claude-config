# MET Norway Locationforecast 2.0 API

## Endpoint
`https://api.met.no/weatherapi/locationforecast/2.0/compact?lat={lat}&lon={lon}`

## Key Details
- **CORS:** Fully open, no proxy needed (unlike NVE which requires Vite proxy)
- **Auth:** No API key. Requires `User-Agent` header (e.g. `alpine-wind/1.0 github.com/edevardHvide/alpine-wind`)
- **Data source:** MEPS 2.5km NWP model — terrain-aware wind forecasts
- **Resolution:** Hourly for ~2.5 days, then 6-hourly out to ~10 days
- **Response:** JSON with `timeseries[]`, each entry has `data.instant.details` (wind_speed, wind_from_direction, air_temperature) and `data.next_1_hours.details` (precipitation_amount)
- **Wind quality:** 6-14 m/s at summits, realistic for alpine terrain (vs NVE's 0.5-3.7 m/s)

## Why MET over NVE for Forecast Wind
NVE seNorge is observation-interpolated 1km grid — fundamentally underestimates summit wind because weather stations are in valleys/sheltered locations. MET uses MEPS numerical weather prediction model that accounts for terrain effects on wind.
