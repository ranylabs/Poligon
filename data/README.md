# Eastern Mediterranean SAR/FIR Reference Layer

This directory contains `srr-eastmed-reference.geojson`, a **non-operational** reference overlay for Poligon.

## Scope and confidence

| Feature | Geometry | Source | Notes |
| --- | --- | --- | --- |
| Cyprus / Nicosia (LCCC) | Polygon | Cyprus AIP ENR 2.1, effective 3 October 2024 | Coordinates transcribed; published 45 and 46 NM arcs are interpolated using spherical geodesics. Full **FIR reference**, not an authenticated GISIS SRR boundary export. |
| Israel / Tel Aviv (LLLL) | LineString | Israel AIP ENR 2.1, effective 6 August 2026 | **Partial maritime boundary only**; 46 NM radius arc interpolated. The 27 NM coastline-parallel section is connected schematically and is not an exact digitization of the coastline-parallel curve. Inland / land boundary is omitted. |
| Egypt / Cairo (HECC) | LineString | ICAO MID ATM SG/1-WP/7 (31 May 2014) | **Partial northern / eastern maritime boundary only**, using historical published FIR coordinates. Current accuracy and full boundary are *not* established. |

The bilateral Israel–Cyprus SAR agreement describes the parties' SRRs as corresponding to their FIRs. Egypt–Greece SAR cooperation also links Egypt's SRR to Cairo FIR. **That correspondence does not validate this file as an official SAR jurisdiction layer.** A valid GISIS or authority-provided SRR geometry should supersede this reference.

## Primary sources

- [Cyprus AIP ENR 2.1](https://www.mcw.gov.cy/mcw/dca/AIS/ais.nsf/All/455773618044F4C9C2257C7E00234503/$file/LC_Amdt_A_2024_004_en.pdf)
- [Israel AIP ENR 2.1](https://e-aip.azurefd.net/2026-08-06-AIRAC/html/eAIP/LL-ENR-2.1-en-GB.html)
- [ICAO MID ATM SG/1-WP/7 (2014)](https://www.icao.int/MID/Documents/2014/ATM%20SG1/WP%207.pdf)
- [Israel–Cyprus SAR Agreement (UN Treaty Series)](https://treaties.un.org/doc/Publication/UNTS/Volume%202981/v2981.pdf)
- [IMO Global SAR Plan](https://www.imo.org/en/OurWork/Safety/Pages/GlobalSARPlan.aspx)

## Coordinate system

GeoJSON standard: **WGS84 longitude, latitude**. Not latitude, longitude. The polygon is closed.

## Use in Poligon

Check **Eastern Mediterranean reference overlay** in the SAR/FIR section to load this file. It does not alter operator-drawn objects or buffers.

Use **Import GeoJSON layer** for a separately obtained, rights-cleared dataset. Do not automatically reinterpret EEZ or national-border polygons as SAR regions.

## Future global coverage

Not supplied. An authoritative, consistently licensed, worldwide maritime SRR GeoJSON dataset has not been verified. The IMO GISIS Global SAR Plan is the appropriate source to consult for validated current data.
