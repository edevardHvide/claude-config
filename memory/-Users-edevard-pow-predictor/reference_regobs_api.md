---
name: RegObs API v5 Quirks
description: RegObs v5/Search ignores lat/lng/radius — must use SelectedRegions; response uses top-level fields not Registrations[].FullObject
type: reference
---

RegObs API v5/Search endpoint quirks discovered 2026-03-26:

- **Geo-filtering broken:** `Latitude`, `Longitude`, `Radius` params are silently ignored. Must use `SelectedRegions: [regionId]` with NVE forecast region IDs.
- **Response structure:** Top-level fields (`SnowSurfaceObservation`, `AvalancheEvaluation3`, `WeatherObservation`, etc.), not `Registrations[].FullObject`.
- **Competency field:** `Observer.CompetenceLevelTID` (not `CompetencyLevel`).
- **Region lookup:** `findRegionIds()` in `src/api/regobs.ts` maps lat/lng to closest region(s). Full region table in `FORECAST_REGIONS` array.
- **API URL:** `https://api.regobs.no/v5/Search` (POST, JSON body).
- **Swagger (limited):** `https://api.regobs.no/v5/swagger/docs/V5` — schema is incomplete.
- **Python client reference:** `https://github.com/NVE/regobslib` — uses `SelectedRegions` approach.
