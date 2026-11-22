# SAR / FIR GIS overlays — Poligon

**Status: reference-only. Not an IMO GISIS-certified global SRR layer.** Updated 22 November 2026.

## Eastern Mediterranean bundled GeoJSON

`srr-eastmed-reference.geojson` contains three source-attributed geometries in WGS84 / GeoJSON **longitude, latitude** coordinate order.

| Region | Geometry | Reference | Completeness |
| --- | --- | --- | --- |
| Cyprus / Nicosia FIR | Closed polygon, 82 coordinates | Cyprus AIP ENR 2.1, May 2026 | FIR described at minute-level precision. The published 45 NM / 46 NM arcs are approximated geodesically. IMO GMDSS 2024 says certain Cyprus/Türkiye/Greece maritime SRR boundaries remain provisional. |
| Israel / Tel Aviv FIR | Open line, 52 coordinates | Israel AIP ENR 2.1, effective August 2026 | Offshore west edge and 46 NM BGN arc only. The 27 NM offshore coast-parallel segment **cannot** be reproduced exactly from the published endpoints alone and is schematic. This is **not** a completed Israeli SRR polygon. |
| Egypt / Cairo FIR | Open line, 5 published coordinates | ICAO MID ATM SG/1 WP/7, June 2014 | Historic northern/eastern FIR reference only; not reverified against the active 2026 Egypt AIP. This is **not** a completed Cairo SRR polygon. |

### Sources

- [Israel AIP ENR 2.1 — effective 06 Aug 2026](https://e-aip.azurefd.net/2026-08-06-AIRAC/html/eAIP/LL-ENR-2.1-en-GB.html)
- [Israel AIP GEN 3.6 — SAR service responsible within Tel Aviv FIR](https://e-aip.azurefd.net/2026-08-06-AIRAC/html/eAIP/LL-GEN-3.6-en-GB.html)
- [Cyprus AIP AIRAC AMDT 002/26 — ENR 2.1](https://www.mcw.gov.cy/mcw/dca/ais/ais.nsf/All/455773618044F4C9C2257C7E00234503/$file/LC_Amdt_A_2026_002_en.pdf)
- [ICAO MID ATM SG/1-WP/7 — Cairo FIR, 2014](https://www.icao.int/MID/Documents/2014/ATM%20SG1/WP%207.pdf)
- [IMO Global SAR Plan (GISIS)](https://www.imo.org/en/ourwork/safety/pages/globalsarplan.aspx)
- [IMO documents relevant to SAR](https://www.imo.org/en/ourwork/safety/pages/imo-documents-relevant-to-sar.aspx)

**Do not infer maritime SRR from EEZ boundaries or national borders.** FIR is not a universal substitute for SRR, even where bilateral/national documents associate them. A SAR boundary does not establish or prejudice state borders or sovereignty.

## Additional worldwide coverage (not a global atlas)

Poligon offers optional **on-demand** public ArcGIS GeoJSON layers, kept separate from the bundled data:

1. **South Pacific** — Search_and_Rescue_Regions_view from an AMSA / IMO-attributed service (data edit 2023). Includes Australia, New Zealand and several Pacific regions; not all oceans. Original source is [ArcGIS FeatureServer layer 2](https://services.arcgis.com/UpqbsAzIhYvD0Asu/ArcGIS/rest/services/Search_and_Rescue_Regions_view/FeatureServer/2).
2. **Canada** — public [ArcGIS Search and Rescue Regions layer 5](https://services3.arcgis.com/1sDiDopq6e43QrCK/arcgis/rest/services/SAR_AGOL_data/FeatureServer/5), coverage and re-use terms must be checked.

External layers load only on request and require online access. We do **not** bundle, copy or redistribute their geometry in this repository. They may fail due to provider changes, CORS, size limits or policy restrictions.

Neither collection is represented as a current or complete worldwide IMO SRR dataset.

## Load authoritative GISIS GML

The website also imports GML files from the IMO's Global SAR Plan system or other authorized institutions. Importing GML does not itself authenticate its origin.

- Click **Import IMO GISIS GML** under *Search & Rescue Regions*.
- The parser supports `gml:MultiSurface` with multiple `gml:Polygon` elements, `gml:exterior`, `gml:interior` and `gml:posList` / `gml:pos`.
- **IMO COMSAR.1/Circ.61 specifies longitude then latitude in `posList`** (not the user-facing lat/lon display order).
- Imported polygons are separate reference layers, with individual color controls.
- Use **Export imported GeoJSON** to convert and retain the layer; this does not verify its authority.
- A free read-only IMO web account may be needed to access GISIS. Do not assume that a bulk global export is offered.

## Layer UX and persistence

- Reference layer colors are stored per feature in the **current browser** under `poligon-srr-colors-v2`. They can be changed independently from operator-created objects.
- Reference layers are drawn in a lower Leaflet map pane, so they do not block existing user objects.
- While **Measure** mode is active, clicking an operator point marker snaps to its exact coordinate, and clicking any segment or polygon interior adds a measurement waypoint.
- The imported GML/GeoJSON itself is session-local until manually exported; the operator objects and measurements use their existing localStorage save.

## Safety and data quality

Never use these reference overlays by themselves to decide which RCC has coordination responsibility in an actual distress case. Obtain and validate current official SAR coordinates from the relevant national authority / IMO GISIS, check special arrangements and overlaps, and record source and effective date before operational adoption.
