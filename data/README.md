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

The 46 NM arc was also recalculated with **WGS84 ellipsoidal geodesic destinations** from the published BGN DVOR coordinates; 47 intermediate points lie on the 46 NM ellipsoidal circle, while the two published AIP rounded endpoints are preserved. The last coastline-parallel section previously appeared as a **single straight segment**, which did not follow coastline curvature. The revised map includes 27 points over this section. These were calculated from the intermediate-resolution **GSHHG shoreline** (via Basemap 2.0) offset seaward in a local azimuthal equidistant projection, then its curvature was smoothly constrained between the two **published AIP endpoint coordinates**. GSHHG coastline data are not themselves official FIR or SAR limits.

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

## Gaza / Rafah discrepancy (reference map vs Poligon)

The existing **Israel / Tel Aviv FIR** southern maritime boundary is anchored at **31°18′N 034°13′E** and **31°50′N 034°00′E**, as specified in the Israeli AIP ENR 2.1 effective August 2026. Connecting these points with a straight segment is correct for this **FIR reference**. The AIP GEN 3.6 states Israeli SAR service responsibility within Tel Aviv FIR, but the FIR reference geometry is **not proof that an independently displayed maritime SRR polygon should include every other local boundary detail**.

The screenshot of Global SAR Hub shows a southern notch close to the Gaza coastline that is **not directly described by this AIP segment**. We have **not established** from the screenshot whether the notch represents political coastline, a separate maritime notice, a distinct SAR polygon, or a different source/boundary revision. We therefore **have not edited the AIP boundary to imitate it.**

A **separately toggleable navigational-warning layer**, `gaza-maritime-notice-ntm1-2009.geojson`, is provided for context. Its 4 positions are transcribed from an RCC Haifa NAVTEX relay of NTM 1/2009 (broadcast Nov 3, 2025; public receipt in Sep–Nov 2026):

| Vertex from notice | Latitude | Longitude |
| --- | --- | --- |
| 1 (coast north) | 31°35.71′N | 034°29.46′E |
| 2 (offshore NW) | 31°46.80′N | 034°10.01′E |
| 3 (coast south) | 31°19.39′N | 034°13.11′E |
| 4 (offshore SW) | 31°33.73′N | 033°56.68′E |

For a valid non-self-crossing GeoJSON polygon, the geographic ring is ordered 1→2→4→3→1. This makes a **NAVTEX maritime notice reference, not a SAR boundary and not a Gaza political boundary**. Source: [RCC Haifa NAVTEX PA06 archive](https://navtex.online/messages/33759). The continued validity of the notice is not confirmed by this source alone.

### Default visibility

- The **East Mediterranean reference** master checkbox is ON at every app launch.
- The **Israel** checkbox is ON at every app launch (even if turned off during a previous session). The operator can switch it off and back on at any time.
- Cyprus, Egypt and other regional boundaries can be selected individually; their existing settings otherwise persist.
- The **Gaza maritime NAVTEX notice** checkbox is OFF by default; it can be enabled independently and uses its own adjustable amber line color.
- The separate Gaza maritime notice does **not** alter the Israel FIR geometry, NOR any stored user objects or measurements.

**Follow-up for exact match:** obtain a current authority-provided Israel maritime SAR polygon / GML from IMO GISIS or JRCC, including any southern coastal exception. Validate origin, effective date and whether the notch is a SAR boundary before replacing a region dataset.

## Israel offshore-to-coast **visual polygon** (22 Nov 2026)

**This is an illustrative coastline-filled map shape, NOT a certified maritime Search and Rescue Region.**

The map has two Israel display options. By default the reference category shows the **shaded illustrative coastal polygon** (`israel-gaza-coastal-composite-illustrative.geojson`), with a persistent map-level warning. Switching the Israel option to **Published Tel Aviv FIR line — AIP** displays the unmodified AIP offshore line instead.

### Independent inputs used to draw the illustrative polygon

1. **Israel AIP ENR 2.1, effective 6 August 2026:** published offshore vertex coordinates and a WGS84-approximated 46 NM arc around BGN VOR. The AIP line from 31°50′N 034°00′E onwards is not an entire coastal SAR polygon.
2. **US NGA Sailing Directions Publication 140, Security Area 605:** positions 31°42′30″N 034°17′35″E and 31°35′43″N 034°29′28″E used as **illustrative southern coastal corner**. These NGA security area vertices are **not** SRR vertices.
3. **Open coastline:** shoreline derived from a merged Israel + Palestinian territories land polygon, downloaded from [roeimichael/Israele](https://github.com/roeimichael/Israele/blob/main/data/israel.geojson), which was compiled from [geoBoundaries gbOpen](https://www.geoboundaries.org/), then simplified into ~0.3 NM latitude samples. The coastline closes the shape northward.
4. **Unpublished illustrative extension:** the southern curved western edge extends the BGN 46 NM circle approximately to 31°33′N 034°09′E for visual comparison, **without an official publication authorizing that extension as a SAR boundary**.

The resulting polygon contains 397 ring positions, is closed and has no detected self-crossings. It is colored translucently and dashed so it is distinguishable from certified boundary data. It is a cartographic illustration and does not claim to reproduce, derive or certify the proprietary Global SAR Hub SRR dataset.

### Shoreline source licensing and attribution

The data derive from geoBoundaries `gbOpen`, with original country-layer licensing verified against their individual metadata:

- [ISR gbOpen ADM0 metadata](https://www.geoboundaries.org/api/current/gbOpen/ISR/ADM0/) identifies **Open Data Commons Open Database License 1.0** (OpenStreetMap/Wambacher source).
- [PSE gbOpen ADM0 metadata](https://www.geoboundaries.org/api/current/gbOpen/PSE/ADM0/) identifies **CC BY 4.0**, based on Sentinel-2 imagery.
- **© OpenStreetMap contributors** and geoBoundaries source teams. The copied coastal sequence in this derivative is attributed here and in the GeoJSON metadata, and identified as modified and simplified.
- Licence text for the ISR underlying data: [ODbL 1.0](https://opendatacommons.org/licenses/odbl/1-0/); PSE layer: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

### Safety / data lineage

NGA restricted maritime areas, airline FIR boundaries, political boundaries, territorial seas, EEZs and maritime SRRs are **not interchangeable**. The completed visual polygon is **not suitable to determine who should coordinate an SAR case**, or to make operational safety decisions.

Only a verified and rights-cleared **IMO GISIS / JRCC-certified SRR GML or GeoJSON** can replace this illustrative polygon as an authoritative layer. The app supports GML import for this purpose, without changing the saved operator geometry.

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

## Workspace UI — saved assets vs editing tools

Poligon separates **Your Workspace** (saved results) from **Map Tools** (actions). This was implemented to avoid confusing a saved measurement with a button:

- Persistent **Your Workspace** section near the top of the left sidebar, with object and measurement counts.
- Saved objects and saved measurements are **non-interactive content cards** with names, type labels, own accent colors, geometry/length metadata and a separate toolbar for Focus, Edit or Rename, Hide/Show and Delete.
- Measurement cards have an amber accent, plotted object cards use their own object color. Clear empty states and a small saved-items counter on the map.
- Deletion requires confirmation. No change to existing project JSON/localStorage formats, and all previously saved measurements/objects remain compatible.
- Tool actions are visually separated below **MAP TOOLS**, and creation/saving buttons receive primary styles.

### Geometry selection directly below coordinates

The Coordinate editor now chooses geometry **at the final save action** rather than via a separate dropdown in Object settings:

- **1 valid coordinate:** one **Save Point** action.
- **2 valid coordinates:** one **Save Route** action.
- **3 or more valid coordinates:** two explicit adjacent actions, **Plot Polygon** (closed area) and **Plot Route** (open polyline).
- If a coordinate row is partially filled or invalid, the save options are hidden until the row is corrected or removed.
- When editing a saved geometry, actions change to **Update as Polygon** and **Update as Route**, with the current geometry highlighted. Saved entities continue using the same JSON format and localStorage key.
- After detection, the editor expands automatically. After successful save, Your Workspace expands and the map shows a brief confirmation.

The old geometry-type dropdown in Object settings was removed to eliminate duplicate, conflicting choices. No polygon is silently selected for 3+ coordinates.

## Right-click map quick actions (November 2026)

Right-click anywhere on the Leaflet map, including a saved polygon/route/point or a reference layer, to open a compact, mouse-positioned **MAP ACTIONS** menu:

- **Measure from here** — starts a distance measurement and records the clicked position as the first waypoint. When measuring is already in progress, the command adds the clicked position as the next waypoint.
- **Add coordinate to editor** — inserts the clicked coordinate as a new row, opens the Coordinate Editor accordion, and leaves operator-saved geometry unchanged until an explicit save.
- **Marine weather here** — opens a dark **Windy-style popup anchored to the selected map coordinate**. It loads Open-Meteo Weather (10 m wind speed/direction/gusts) and Marine (significant wave height/direction/period and ocean-current speed/direction), showing model data for the selected UTC hour. Previous/next hour, Refresh and Details are supported. Source attribution and a nearshore-current warning are displayed.
- **Copy coordinates** — copies the DDM WGS84 pair to the clipboard, with manual copy fallback if clipboard permissions are unavailable.

When a right-click occurs within 10 screen pixels of an **existing visible user geometry vertex**, it snaps exactly to the saved vertex coordinate; otherwise the geographic clicked point is used.

When **Measure** mode is already active, the same menu also shows **Finish & Save, Undo Last Point, Cancel Measurement** at the top. Other actions remain available without silently ending the in-progress measurement.

The popup uses the existing Leaflet map, so it stays anchored correctly while the map pans/zooms. No public API keys are embedded. For the short-form widget, weather and marine HTTP requests run independently; if one service fails but the other succeeds, the available model values remain visible.

**Units / conventions:** Wind speed is in **knots**; wind direction is **FROM**. Significant wave height (Hs) is in **metres**; wave direction **FROM**, wave period **seconds**. Ocean-current direction **TO**; marine model current speed is converted to knots from the unit reported by the API. Invalid or missing values display as unavailable rather than fabricated zeros.

**Safety / licensing:** Open-Meteo model forecasts are *not observations*; the marine current forecast has limited coastal precision. The free API plan may not cover production/commercial/ongoing organizational use; provider terms, credits, and request limits must be checked before operational deployment. The popup is a planning aid only, not for navigation or sole-source SAR coordination.

## November 27, 2026 — Live editing, saved startup visibility, and right-click markers

### Object editing
- Selecting **Edit** opens Object Settings and Coordinate Editor.
- **Name, color, buffer (NM), Show on every visit** are saved immediately using the existing `poligon-v1` localStorage project key. The map and saved Workspace card update without clicking Plot.
- **Coordinate edits** remain pending in the editor until the operator clicks **Update as Polygon** / **Update as Route** / Save Point. This is deliberate to prevent accidental geometry changes.
- The live-edit status panel explicitly describes the difference. Deleting an object under edit resets the editor; deleting an earlier object adjusts the selected index.

### Startup visibility
- Each object stores `autoLoad` (boolean). The editor and saved Workspace card both expose **Show on every visit**.
- **Default:** checked for newly saved polygons/routes/points and right-click quick markers. Old projects without the property also default to checked.
- On each fresh page load, every saved object is **loaded into Workspace**, but only `autoLoad !== false` objects are displayed on the map. Other objects remain in Workspace, available using Show.
- **Hide / Show** controls visibility in the current browser session; **Show on every visit** determines visibility on the next startup. A temporarily hidden object whose autoLoad remains checked reappears at the next visit.
- Project JSON exports include this setting; older Line and V4-style JSON arrays are normalized on import.

### Immediate marker
- Right-click the map and choose **Add marker here (save now)**. A named, colored **map pin** is saved immediately, with `type: "Point"`, `quickMarker: true`, and `autoLoad: true`, without using Plot.
- Marker is visible and listed in Your Workspace, with Edit / Focus / Hide / Delete and Show on every visit.
- **Add coordinate to editor** remains a separate operation; it does not create a saved marker until the user plots it.

### Interface
- All eight sidebar accordion panels (including **Your Workspace**) are **closed by default** at new page load.
- Editing opens only its relevant panels; saving an object/measurement opens Workspace.
- The Leaflet basemap and seamark layer chooser now uses a consistent high-contrast dark background, light text, visible radio/checkbox selectors and improved spacing.

**QA performed:** GitHub source syntax checks and pure-JS scenario tests for property mutation, legacy project parsing, startup visibility, marker creation and menu availability. **Not yet verified:** live click-through browser QA, CDN responsiveness, GitHub Pages deployment completion. 

## Layer UX and persistence

- Reference layer colors are stored per feature in the **current browser** under `poligon-srr-colors-v2`. They can be changed independently from operator-created objects.
- Reference layers are drawn in a lower Leaflet map pane, so they do not block existing user objects.
- While **Measure** mode is active, clicking an operator point marker snaps to its exact coordinate, and clicking any segment or polygon interior adds a measurement waypoint.
- The imported GML/GeoJSON itself is session-local until manually exported; the operator objects and measurements use their existing localStorage save.

## Safety and data quality

Never use these reference overlays by themselves to decide which RCC has coordination responsibility in an actual distress case. Obtain and validate current official SAR coordinates from the relevant national authority / IMO GISIS, check special arrangements and overlaps, and record source and effective date before operational adoption.
