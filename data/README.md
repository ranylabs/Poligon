# SAR / FIR GIS overlays — Poligon

**Status: reference-only. Not an IMO GISIS-certified global SRR layer.** Updated 22 November 2026.

## Eastern Mediterranean bundled GeoJSON

`srr-eastmed-reference.geojson` contains **six** source-attributed geometries in WGS84 / GeoJSON **longitude, latitude** coordinate order. Unless otherwise stated, these are FIR-linked references, not operationally verified maritime SRR polygons.

| Region | Geometry | Reference | Completeness |
| --- | --- | --- | --- |
| Cyprus / Nicosia FIR | Closed polygon, 82 coordinates | Cyprus AIP ENR 2.1, May 2026 | FIR described at minute-level precision. The published 45 NM / 46 NM arcs are approximated geodesically. IMO GMDSS 2024 says certain Cyprus/Türkiye/Greece maritime SRR boundaries remain provisional. |
| Israel / Tel Aviv FIR | Open line, 52 coordinates | Israel AIP ENR 2.1, effective August 2026 | Offshore west edge retains exact published AIP anchors and the 46 NM BGN arc. The 27 NM northern coastline-parallel segment has been reshaped using GSHHG intermediate-resolution shoreline curvature, with the published endpoints fixed. **This is a cartographic reconstruction, not an officially surveyed 27 NM equidistant line or a completed Israeli SRR polygon.** |
| Egypt / Cairo FIR | Open line, 5 published coordinates | ICAO MID ATM SG/1 WP/7, June 2014 | Historic northern/eastern FIR reference only; not reverified against the active 2026 Egypt AIP. This is **not** a completed Cairo SRR polygon. |
| Malta / Malta FIR | Closed polygon, 5 vertices | Malta AIP ENR 2.1 / GEN 3.6, June 2026 | Malta AIP states its maritime SAR region coincides with Malta FIR. **FIR geometry reference**, not directly verified against GISIS. |
| Greece / Athens FIR | Open line, 7 vertices | Greek Hydrographic Annual Notices to Mariners 2025 and AIP references | Partial offshore western/southern boundary; Aegean disagreements and non-coastal sides omitted. |
| Lebanon / Beirut FIR | Open line, 38 vertices | ICAO MID ATM SG/9 WP5, 2023 | Partial offshore FIR limit with a geodesically interpolated circular arc. Coast-parallel and inland borders omitted; SRR extent not authenticated. |

### Israel improvement methodology (2026-11-22)

The authoritative source, **Israel AIP ENR 2.1 (effective 2026-08-06)**, publishes:
- Southwest anchor: **31°18′N 034°13′E**, then **31°50′N 034°00′E**.
- A **46 NM** clockwise geodesic arc centred on **BGN DVOR**, whose source location is published in AIP ENR 4.1 / AD 2 as **32°00′47.2″N 034°52′31.3″E**, ending **32°43′N 034°32′E**.
- Next a line **27 NM parallel to the coastline** ending **33°06′N 034°35′E**, then **33°06′N 035°06′E**.

The last coastline-parallel section previously appeared as a **single straight segment**, which did not follow coastline curvature. The revised map includes 27 points over this section. These were calculated from the intermediate-resolution **GSHHG shoreline** (via Basemap 2.0) offset seaward in a local azimuthal equidistant projection, then its curvature was smoothly constrained between the two **published AIP endpoint coordinates**. GSHHG coastline data are not themselves official FIR or SAR limits.

**Geometry caveat:** The AIP gives a distance description, not a sequence of intermediate vertices. With the AIP endpoints fixed, measured distances to the generalized coastline are not uniformly 27 NM; the reconstructed segment is not mathematically identical to a true 27 NM shoreline offset. This is more coast-shaped than the former line, but **cannot be described as a fully precise or authority-certified maritime SRR**.

The screenshot from Global SAR Hub was used only to understand the user's visual concern. **No boundaries were copied or extracted from that provider's map**, which prohibits reproduction or extraction without permission.

GSHHG source: [NOAA NCEI Shoreline Database](https://www.ngdc.noaa.gov/mgg/shorelines/shorelines.html); GSHHG is published under LGPL. See the NOAA page for its licence and attribution requirements.

If GISIS or JRCC Haifa provides the current official SRR GML/GeoJSON, **replace the reference line rather than adding undocumented extra vertices**. Poligon already supports GML and GeoJSON import for that purpose.

### Sources

- [Israel AIP ENR 2.1 — effective 06 Aug 2026](https://e-aip.azurefd.net/2026-08-06-AIRAC/html/eAIP/LL-ENR-2.1-en-GB.html)
- [Israel AIP GEN 3.6 — SAR service responsible within Tel Aviv FIR](https://e-aip.azurefd.net/2026-08-06-AIRAC/html/eAIP/LL-GEN-3.6-en-GB.html)
- [Cyprus AIP AIRAC AMDT 002/26 — ENR 2.1](https://www.mcw.gov.cy/mcw/dca/ais/ais.nsf/All/455773618044F4C9C2257C7E00234503/$file/LC_Amdt_A_2026_002_en.pdf)
- [ICAO MID ATM SG/1-WP/7 — Cairo FIR, 2014](https://www.icao.int/MID/Documents/2014/ATM%20SG1/WP%207.pdf)
- [Malta AIP 2026 — FIR + coincident SAR responsibility](https://www.transport.gov.mt/LM_AIP_2026_83_EFF_11_JUN_2026-2.pdf-f11582)
- [Greek Hydrographic Service Annual NtM 2025](https://hnhs.gr/wp-content/uploads/2024/12/2025_AnnualNM_EN.pdf)
- [ICAO MID ATM SG/9-WP5 — Beirut FIR geometry (2023)](https://www.icao.int/MID/Documents/2023/ATM%20SG9/WP5.pdf)
- [France Shom — official SAR polygons (Open Licence 2.0, original edition 2019)](https://www.data.gouv.fr/datasets/zones-de-recherches-et-secours-sar)
- [Italy — national maritime SAR plan (2020)](https://www.mit.gov.it/sites/default/files/media/normativa/2021-03/PIANO%20SAR%20MARITTIMO%20NAZIONALE%20Ed.%202020_rev.pdf)
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
- Multiple imported GML and GeoJSON files can be **appended** into one reference layer, with individual color controls and an option to hide/show the combined layer.
- If two input files share the same internal Area Number, unique in-session imported IDs prevent color overrides from colliding.
- Use **Export imported GeoJSON** to convert and retain the layer; this does not verify its authority.
- A free read-only IMO web account may be needed to access GISIS. Do not assume that a bulk global export is offered.

## Interactive measuring

- **Measure** works on open map, user-defined points, polylines, polygons, buffers and reference lines.
- Move the pointer to see the **live distance of the next leg**, **true initial bearing (°T)** and **accumulated NM**.
- **Right-click anywhere on the map**, including existing drawn objects, to open a menu: Finish & Save / Undo last point / Cancel.
- Keyboard shortcuts during measurement: **Enter** (finish), **Backspace** (undo), **Esc** (close context menu or cancel measurement).
- Click user-created point markers for exact coordinate snapping. Clicking a line segment uses the clicked geographic position.

## Layer UX and persistence

- Reference layer colors are stored per feature in the **current browser** under `poligon-srr-colors-v2`. They can be changed independently from operator-created objects.
- Reference layers are drawn in a lower Leaflet map pane, so they do not block existing user objects.
- While **Measure** mode is active, clicking an operator point marker snaps to its exact coordinate, and clicking any segment or polygon interior adds a measurement waypoint.
- The imported GML/GeoJSON itself is session-local until manually exported; the operator objects and measurements use their existing localStorage save.

## Safety and data quality

Never use these reference overlays by themselves to decide which RCC has coordination responsibility in an actual distress case. Obtain and validate current official SAR coordinates from the relevant national authority / IMO GISIS, check special arrangements and overlaps, and record source and effective date before operational adoption.
