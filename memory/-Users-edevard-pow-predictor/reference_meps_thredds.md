---
name: MEPS THREDDS Wind Data
description: MEPS 2.5km wind from MET Norway THREDDS OPeNDAP — archive format, latest format, grid params, pressure level indices
type: reference
---

MEPS wind data is available on MET Norway's THREDDS server, no auth needed.

**Archive (historical):** `thredds.met.no/thredds/dodsC/meps25epsarchive/YYYY/MM/DD/meps_det_2_5km_YYYYMMDDTHHZ.nc`
- Goes back to 2016, runs every 3h (00Z, 03Z, ..., 21Z), 67 hourly timesteps per run
- No ensemble dimension. 10m height dim = `height7`. 13 pressure levels, 850hPa = index 10
- OPeNDAP query: `x_wind_10m[t][0][y][x]`, `x_wind_pl[t][10][y][x]`

**Latest (forecast):** `thredds.met.no/thredds/dodsC/mepslatest/meps_lagged_6_h_subset_2_5km_YYYYMMDDTHHZ.ncml`
- 62 timesteps, 30 ensemble members. 10m height dim = `height2`. 6 pressure levels, 850hPa = index 3
- OPeNDAP query: `x_wind_10m[t][0][ens][y][x]`, `x_wind_pl[t][3][ens][y][x]`

**Grid:** Lambert Conformal Conic, origin x=-1060084, y=-1332517.9, spacing 2500m, 949×1069 cells.
**Projection:** lat0=63.3, lon0=15.0, standard_parallel=63.3, R=6371000.

**Key insight:** 850hPa wind matches reality on exposed ridges (~1500m). 10m wind is damped by surface friction in the model. NVE seNorge wind is useless for mountains (5-6x underestimate).
