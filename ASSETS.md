# Asset inventory
 
Reflects assets currently referenced in `index_v2.html`. Unused files have been moved to `assets/images/asset_archive/`.
 
---
 
## Video
 
| File | Used in | Notes |
|------|---------|-------|
| `assets/video/ant_sea_ice_globe.mp4` | Scene 1 | Rotating globe, autoplay muted loop. Falls back to `ant_globe_view.png`. |
| `assets/video/ant_ice_change.mp4` | Scene 3 | Ice retreat footage, muted loop. Falls back to `ant_mass_change.png` on error. |
 
---
 
## Images
 
### Backgrounds and photos
 
| File | Used in | Notes |
|------|---------|-------|
| `ant_globe_view.png` | Scene 1 | Fallback background if globe video fails |
| `antarctic_soils.jpg` | Scene 2 | Soil photo background, beats 0-2 |
| `ant_coast.jpg` | Scene 2, Scene 7 | Geo/coast background, beats 3-6; also Scene 7 card background overlay |
| `ant_mass_change.png` | Scene 3 | Fallback background if ice video fails |
| `soil_core.jpg` | Scene 2 | Soil core photo, beat 6 right panel |
| `ant_fw_camp.jpg` | Scene 4 | Field camp photo, beat 1 full-bleed background |
| `ant_field_work.png` | Scene 7 | Field science card image |
| `ant_dry_valley.png` | Scene 7 | Astrobiology card image |
 
### Maps and data layers
 
| File | Used in | Notes |
|------|---------|-------|
| `acbr_regions.jpg` | Scene 4 | Antarctic Conservation Biogeographic Regions map, beat 0 |
| `samples_real.svg` | Scene 4 | 171 actual sample locations across 4 regions, beat 2 |
| `elevation.png` | Scene 5 | Satellite data grid, beat 0 |
| `precipitation.png` | Scene 5 | Satellite data grid, beat 0 |
| `contours.png` | Scene 5 | Satellite data grid (slope and aspect), beat 0 |
| `lithology.png` | Scene 5 | Satellite data grid, beat 0 |
 
### ML prediction maps
 
All used in Scene 6 map explorer. Files follow the naming convention `clean_NN_propertyname.png`.
 
| File | Property | In HTML |
|------|----------|---------|
| `clean_01_delta-15N.png` | Nitrogen isotopes | Yes |
| `clean_02_phosphorus.png` | Phosphorus | Yes |
| `clean_03_sodium.png` | Soluble sodium | Yes |
| `clean_04_nickel.png` | Nickel | Yes |
| `clean_10_titanium.png` | Titanium | Yes |
 
### Ice retreat slideshow
 
Used in Scene 7, climate science card.
 
- `ice_retreat_1.png` through `ice_retreat_6.png`
---
 
## Source files (illustrator_files/)
 
PDF exports of base map layers, kept for reference and potential re-export.
 
| File | Notes |
|------|-------|
| `all_layouts.pdf` | All map layouts compiled |
| `basemap.pdf` | Base satellite map |
| `elevation.pdf` | Elevation raster source |
| `precipitation.pdf` | Precipitation raster source |
| `lithology.pdf` | Lithology point data source |
| `contours.pdf` | Contour lines source |
| `samples.pdf` | Sample locations source |
| `standard_basemap.pdf` | Clean basemap without overlays |
 
---
 
#### Everything else unused has been moved to `assets/images/asset_archive/`.
