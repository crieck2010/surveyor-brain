# surveyor-brain

**Worked computational notebooks from a practicing field surveyor.**

Most surveying software hides the maths. This repo does the opposite: every notebook
takes a real surveying computation — the kind an instrument person runs in the field
and a licensed surveyor stakes their seal on — and works it in the open, top to
bottom, with the checks a reviewer would demand.

Written by a Colliers Engineering & Design crew chief / instrument person working
toward the FS exam and PLS licensure (UMaine Surveying Technology, May 2027). The
aim is simple: the field-surveyor-who-codes edge, demonstrated — not claimed.

## Notebooks

| # | Notebook | What it works |
|---|----------|---------------|
| 01 | [Traverse closure & Bowditch adjustment](notebooks/01-traverse-closure-bowditch.ipynb) | Five-sided closed loop from a realistic field book: angular misclosure (+4.0″), azimuth carry, latitudes/departures, linear misclosure 0.011 m, **relative precision 1 : 87,947**, compass-rule adjusted coordinates, plotted raw vs adjusted. |
| 02 | [Datums & State Plane — Rochester, NY](notebooks/02-datums-state-plane-rochester.ipynb) | WGS84 → NAD83(2011) → NY West State Plane (EPSG:2262, US survey feet) with `pyproj`: convergence +0.667°, point scale +14.7 ppm, grid-vs-ground distance (+26.7 mm over 1.69 km), round-trip closure ≈ 0.00 mm — plus the two datum traps that actually bite in practice (ballpark "WGS84" shifts, and unit-only "NAVD88" conversions). |

## Rules of the house

- **Every notebook executes cleanly, top to bottom**, with outputs committed — if it
  doesn't run, it doesn't ship. (Verified with `jupyter nbconvert --execute`.)
- **Data is realistic synthetic field data** unless a notebook says otherwise —
  generated to behave like honest instrument work, misclosures included.
- **Methods are the real thing**: angle adjustment before azimuths, Bowditch where
  Bowditch is defensible (and a note on where least squares takes over), official
  EPSG CRS definitions for every transformation.
- Numbers are **checked against an independent computation** before publishing
  (the State Plane factors in notebook 02 are cross-verified by finite differences
  on the transform itself).

## Run them yourself

```bash
pip install -r requirements.txt
jupyter notebook notebooks/
```

## Roadmap

- Least-squares traverse adjustment (and when Bowditch stops being enough)
- Level loop adjustment by proportional distribution
- Geodetic inverse / forward problems on GRS80
- COGO: bearing–bearing and bearing–distance intersections
- Vertical datums with a verified GEOID18 workflow

## License

MIT — see [LICENSE](LICENSE). Notebooks are teaching material; field procedures on
real projects belong to the supervising licensee, as always.
