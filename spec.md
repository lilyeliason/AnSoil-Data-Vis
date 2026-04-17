# The 0.18% — Design Specification
 
Current as of `index_v2.html`. 8 scenes total.
 
---
 
## Tech Stack
 
- Vanilla HTML, CSS, JavaScript only. No frameworks.
- Scrollama.js for scroll triggering (CDN: https://unpkg.com/scrollama)
- D3 v7 for data visualization (CDN: https://cdn.jsdelivr.net/npm/d3@7)
- No jQuery, no React, no Vue.
---
 
## Color System
 
```css
--color-bg:             #0A1628;
--color-text-primary:   #E8F4F8;
--color-text-secondary: #4A9ECA;
--color-dig-deeper:     #2D6E7E;
--c-bg-panel:           #0D1E35;
--c-ice-shadow:         #5A88AA;
--c-teal-light:         #3D8FA2;
--c-border:             rgba(74,158,202,0.18);
--c-overlay:            rgba(10,22,40,0.74);
```
 
---
 
## Global UI Elements
 
- Fixed right-side progress dots, one per scene, highlight as reader advances. 9 dots total (Scene 8 is credits placeholder).
- Fixed "Dig Deeper" button, bottom right, color `#2D6E7E`. Appears from Scene 2 onward. Slides up when Scene 3 (climate video) is active to avoid covering the panel. Opens a slide-in panel from the right.
- Dig Deeper panel content is not yet scene-specific — panel opens with a generic heading.
---
 
## Asset Paths
 
All assets live under `assets/`. See `ASSETS.md` for the full inventory.
 
```
assets/video/
  ant_sea_ice_globe.mp4
  ant_ice_change.mp4
 
assets/images/
  ant_globe_view.png
  antarctic_soils.jpg
  ant_coast.jpg
  ant_mass_change.png
  soil_core.jpg
  ant_fw_camp.jpg
  ant_field_work.png
  ant_dry_valley.png
  acbr_regions.jpg
  samples_real.svg
  elevation.png
  precipitation.png
  contours.png
  lithology.png
  clean_01_delta-15N.png
  clean_02_phosphorus.png
  clean_03_sodium.png
  clean_04_nickel.png
  clean_10_titanium.png
  ice_retreat_1.png through ice_retreat_6.png
```
 
---
 
## Scene 1 — The 0.18%
 
**Layout:** Full-bleed, dark background `#0A1628`. Sticky graphic for the full scene height (260vh).
 
**Background:** Globe video (`ant_sea_ice_globe.mp4`), autoplay muted loop, covers full viewport. Falls back to `ant_globe_view.png` if video fails.
 
**On load:**
- Title fades in centered: "The 0.18%"
  - Font: large, weight 300, `--color-text-primary`
- Subtitle below: "Predicting Antarctic Soil Geochemistry"
  - Font: small, letter-spaced, `rgba(232,244,248,0.55)`
- Scroll cue: animated down arrow + vertical line, fades on first scroll
**Scroll sequence (triggered by scroll depth into scene):**
- Title fades out after ~60px of scroll
- Scroll cue hides after ~40px
- At ~220px depth: `s1-text-1` fades in (top left)
  - "Antarctica is buried under a dense blanket of ice, spanning 14.2 million square kilometers, making it the largest mass of ice on Earth"
- At ~420px depth: `s1-text-2` fades in below, orange blob flecks activate
  - "Less than **0.18% of this continent is ice-free**. And in that fraction lies almost all of Antarctica's biodiversity"
**Blob flecks:**
- SVG overlay of 10 orange circles (`#FF8C3A`) positioned over ice-free regions of Antarctica
- Glow filter applied (`feGaussianBlur` stdDeviation 18)
- Animate with `blobPulse` keyframes (opacity 0.45 to 0.90, staggered delays) when `.is-active` class is present
- Scale transform: `scale(0.41)` centered on the Antarctica continent position
---
 
## Scene 2 — Why Soils Matter
 
**Layout:** Sticky graphic (620vh). Two overlapping phases sharing the same sticky container — soil phase (beats 0-2) and geo phase (beats 3-6) — cross-fading via opacity transitions.
 
### Soil phase (beats 0-2)
 
**Background:** `antarctic_soils.jpg`, opacity 0.35, with dark gradient overlay.
 
**Left side — text stack** (`s2soil-text-stack`):
One text block visible at a time, centered vertically, opacity transition.
 
- Beat 0: "And in those exposed regions and buried deep beneath the ice, lies something most people never think about. **The soil**"
- Beat 1: "These arid, gravelly soils are shaped by extreme cold and dry circumstances. These conditions have resulted in **unique geochemistry** that serves as the baseline for everything that can survive here."
- Beat 2: "Despite low biological activity relative to other ecosystems, these soils support a diverse and unique set of organisms. **Without these unique conditions and soils as a baseline, none of this life could survive**"
**Right side — ecosystem pyramid** (`s2soil-diagram`):
SVG pyramid with 6 tiers, building bottom-up. Fades in at beat 1. All tiers visible at beat 2.
 
Tiers (bottom to top):
1. Soil Chemistry — `rgba(232,105,154)`
2. Bacteria, Fungi & Cyanobacteria — `rgba(164,125,171)`
3. Mites, Nematodes & Tardigrades — `rgba(60,120,200)`
4. Mosses, Lichens & Flora — `rgba(74,158,202)`
5. Krill, Icefish & Benthos — `rgba(74,202,158)`
6. Seals, Whales & Penguins — `rgba(232,196,74)`
### Geo phase (beats 3-6)
 
**Background:** `ant_coast.jpg`, opacity 0.18 (drops to 0.06 at beat 6), with dark overlay.
 
- Beat 3 (`s2geo-beat-a`): "Thousands of expeditions have been made over a century of Antarctic research"
- Beat 4 (`s2geo-beat-a2`): "**And yet the geochemistry of these soils remains largely unmapped**"
- Beat 5 (`s2geo-beat-a3`): "These soils are **barometers of environmental change**. If we can't understand them, we can't track what's changing, or what's being lost."
- Beat 6 (`s2geo-beat-b`): Split layout — `soil_core.jpg` photo left, properties panel right.
**Beat 6 properties panel:**
- Title: "What Soil Chemistry Reveals"
- Body: "Soil is a chemical record of an ecosystem, climate, and geology of the area. It's made up of dozens of unique chemical properties that give us specific insights into different aspects of Antarctic conditions"
- Bubble tags: pH & Electrical Conductivity, Water-Soluble Ions, Nutrient Availability, Heavy & Trace Metals, Isotopic Signatures, Total Carbon & Nitrogen
**Beat thresholds** (scroll progress through scene):
- 0-12%: beat 0
- 12-28%: beat 1
- 28-42%: beat 2
- 42-55%: beat 3
- 55-65%: beat 4
- 65-78%: beat 5
- 78-100%: beat 6
---
 
## Scene 3 — Conditions Are Changing
 
**Layout:** Sticky graphic (280vh). Full-bleed video.
 
**Background:** `ant_ice_change.mp4`, muted loop, scale(1.12) to avoid letterboxing. Falls back to `ant_mass_change.png` on error. Dark overlay `rgba(10,22,40,0.55)`.
 
**Play button:** Centered, appears if video hasn't autoplayed. Hides once playing.
 
**Scroll sequence (by progress through scene):**
- 0-33%: Title fades in centered — "And Antarctica is changing."
  - Video begins playing on entry
- 33-66%: Title hides. Play button shows if video isn't playing.
- 66-100%: Frosted-glass panel fades in, bottom right.
  - "As the climate warms, the ice is retreating and exposing soils that have been frozen for thousands of years. These soils hold valuable records of carbon, microbial life, and ecosystem history. Without geochemical baselines, we have no way to track what is changing."
**Dig Deeper button:** Raised to `bottom: 80px` during this scene to avoid overlapping the panel.
 
---
 
## Scene 4 — The Sampling Problem
 
**Layout:** White background (`#ffffff`). Sticky graphic (380vh). 3 beats.
 
**Beat thresholds:**
- 0-33%: beat 0
- 33-66%: beat 1
- 66-100%: beat 2
### Beat 0 — One approach
 
Centered column layout. Dark text on white.
 
- Body: "One approach to understanding these soils is to take a diverse and wide array of samples from across all 28 ice-free regions and analyzing their geochemical properties in a lab"
- Map: `acbr_regions.jpg` centered below text
- Caption: "Antarctic Conservation Biogeographic Regions (ACBRs)"
### Beat 1 — But sampling everywhere isn't realistic
 
Full-bleed `ant_fw_camp.jpg` left. Dark frosted panel right.
 
Panel heading: "**But sampling everywhere isn't realistic**"
 
Barrier list:
- $ Expensive — "Each expedition costs tens of thousands of dollars per sample site."
- ⏱ Time-consuming — "Each site requires days of preparation."
- ⚑ Logistically difficult — "Extreme cold, remoteness, and limited field stations."
### Beat 2 — The reality
 
Split layout, dark background. Text left, map right.
 
- Label: "The reality"
- Headline: "For the entire continent, our lab has analyzed the geochemistry of only **171 samples** in **4 regions**"
- Sub: "Ideal coverage would require thousands of samples from all 28 ACBR regions. What we have is a mere fraction of that."
- Map: `samples_real.svg` in a white-background frame
- Caption: "171 samples · 4 regions · 28 locations"
- Legend: NW Antarctic Peninsula `#da3832`, Transantarctic Mountains `#a47dab`, South Victoria Land `#6a9295`, North Victoria Land `#6db85c`
---
 
## Scene 5 — The Approach
 
**Layout:** Dark background `--color-bg`. Sticky graphic (380vh). 3 beats.
 
**Beat thresholds:**
- 0-33%: beat 0 (satellite data)
- 33-55%: beat 1 (pivot line)
- 55-100%: beat 2 (equation)
### Beat 0 — Satellite data
 
Split layout. Text left, 2x2 image grid right.
 
- Label: "Open Source Satellite Data"
- Headline: "Satellites can observe the physical properties of every square meter of Antarctica's surface, whether anyone has been there or not."
- Sub: "We have sourced 9 environmental satellite-derived spatial layers of map data"
- Variable list: Lithology, Distance to Coast, Elevation, Mean Annual Temperature, Mean Annual Precipitation, Slope & Aspect, Latitude, Longitude
Image grid (reveals with staggered delay on beat entry):
- `elevation.png` — Elevation
- `precipitation.png` — Precipitation
- `contours.png` — Slope & Aspect
- `lithology.png` — Lithology
### Beat 1 — Pivot
 
Centered text, bordered top and bottom:
"**However, there is another way to look at Antarctica, one that doesn't require a single expedition**"
 
### Beat 2 — Equation
 
Centered column. Circular icon terms connected by + signs and an arrow.
 
- Label: "The approach"
- Headline: "By combining satellite data with our samples, we can make **predictions**"
- Sub: "Machine learning algorithms learn the relationships between our satellite data and our soil samples to make predictions about the geochemistry in places we've never been before."
Equation terms (left to right):
1. 171 Soil Samples — "Known Spatial Data, Known Geochemistry" — purple icon
2. + Satellite Data — "Known Spatial Data, Unknown Geochemistry" — blue icon
3. + Machine Learning — "3 ML Models trained on both data types" — amber icon
4. → Predicted Geochemistry — "Continent-wide predicted soil chemistry" — pink/coral output circle
---
 
## Scene 6 — Explore the Predictions
 
**Layout:** Dark background. Sticky graphic (20vh scroll). Interactive — not scroll-driven.
 
**Map area:** Full-bleed prediction map images, stacked absolutely. One active at a time, opacity transition 0.8s.
 
**Left panel** (`s7-info-panel`):
- Title: "Explore the Predictions"
- Sub: "Select a property to overlay ML-predicted geochemistry across the continent. Each map reveals a distinct environmental signal."
- Active info box: shows property name, "Why does it look like this?" label, and explanation text. Updates on tab selection.
**Right tab strip** (`s7-tabs-panel`):
Vertical strip, full viewport height minus 80px. One tab per property. Active tab shows colored left bar and highlighted label.
 
Current tabs and maps:
 
| # | Label | Map file | Color |
|---|-------|----------|-------|
| 01 | Nitrogen Isotopes | `clean_01_delta-15N.png` | `#e87878` |
| 02 | Phosphorus | `clean_02_phosphorus.png` | `#78c8a0` |
| 03 | Sodium | `clean_03_sodium.png` | `#4A9ECA` |
| 04 | Nickel | `clean_04_nickel.png` | `#c4a47d` |
| 05 | Titanium | `clean_10_titanium.png` | `#9ab0c8` |
 
**Planned additions** (clean_05 through clean_09 not yet wired up):
Magnesium, Molybdenum, Nitrogen, Potassium, Phosphate.
 
**Info pane content:**
 
- Default (no selection): "Select a property →" / "Each layer reveals a different environmental driver shaped by millions of years of Antarctic isolation."
- δ¹⁵N: "Coastal hotspots trace penguin rookeries and seal colonies whose waste enriches marine-derived nitrogen. Inland deserts, devoid of animals, show none of this signature."
- Phosphorus: "Phosphorus concentrations track both bedrock weathering and biological inputs. Coastal zones with high animal activity show elevated values from guano and organic matter decomposition."
- Sodium: "A fading ring around the continent's edges maps the marine aerosol footprint. Coastal winds deposit sea salt directly onto soil; the Transantarctic Mountains block this inland."
- Nickel: "Nickel distribution closely follows mafic and ultramafic rock formations. Its sharp boundaries are a near-perfect trace of igneous intrusions across ice-free zones."
- Titanium: "Stark jagged boundaries trace the Ferrar Dolerite volcanic formations almost perfectly. Chemical weathering is so slow here that bedrock lithology dominates the signal entirely."
---
 
## Scene 7 — Why It Matters
 
**Layout:** Dark background with `ant_coast.jpg` at 6% opacity. Three equal-width cards side by side, full viewport height. Dividers between cards. Sticky graphic (20vh scroll).
 
### Card 1 — Climate Science
 
- Label: "Climate Science"
- Title: "Tracking a changing continent"
- Body: "As ice retreats and new soils emerge, we have no baseline for what they contain. Geochemical predictions give us that baseline — so we can measure what is being lost or created as the planet warms."
- Visual: Slideshow cycling through `ice_retreat_1.png` through `ice_retreat_6.png`, 2200ms interval, crossfade 1.2s
### Card 2 — Field Science
 
- Label: "Field Science"
- Title: "Smarter expeditions"
- Body: "Continent-wide prediction maps tell future researchers exactly where the most scientifically valuable sites are — saving time, money, and the enormous logistical costs of Antarctic fieldwork."
- Visual: `ant_field_work.png`, static
### Card 3 — Astrobiology
 
- Label: "Astrobiology"
- Title: "A window to other worlds"
- Body: "Antarctic ice-free soils are our closest analogue on Earth to the surface of Mars. Understanding what survives here — and why — is a guide to where we might search for life beyond our planet."
- Visual: `ant_dry_valley.png`, static
---
 
## Scene 8 — Credits
 
Not yet built. Placeholder div present in HTML.
 
Content to include:
- Research data: BYU LeMonte Lab
- Visualization: Lily Eliason
- Course: DSPX315
- Image and data credits
---
 
## Implementation Notes
 
1. All scene transitions are scroll-driven via a single `window.scroll` listener, not Scrollama step triggers (Scrollama is initialized but only used for `.step` class elements, currently unused). Scene progress is calculated as `scrolled / (scene.offsetHeight - window.innerHeight)`.
2. Scene 2 is the most complex — 7 beats, two background cross-fades, a pyramid SVG, and a split layout all within one sticky container. Beat thresholds are percentage-based, defined in the scroll handler.
3. Scene 6 is fully interactive and not scroll-driven. Tab clicks swap map layers and info panes directly via JS event listeners.
4. The Dig Deeper button is positioned `fixed`, bottom right. It raises to `bottom: 80px` during Scene 3 to avoid overlapping the frosted panel. This is handled in `updateDigVisibility()`.
5. Progress dots are generated dynamically for 9 scenes. Active dot updates in `updateDotFromScroll()` based on which scene's `offsetTop` the midpoint of the viewport has passed.
6. Videos use `play().catch()` to handle autoplay blocking gracefully. Scene 1 globe video hides itself on error. Scene 3 video shows a play button if autoplay fails.
7. White-background scenes (Scene 4) require text color overrides — the global `--color-text-primary` is light-colored and invisible on white. Scene 4 uses hardcoded dark text values (`#1a1a1a`, `rgba(0,0,0,0.55)`) throughout.
