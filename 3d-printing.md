# 3D Printing

This is about calibrating the Creality Ender 3 V3 SE for PETG filament.


### The challenge

1. PETG was stringing heavily.
1. Reducing temperature helped with stringing, but introduced ripping. Long laid lines would fail to bond cleanly and get pulled up, especially on the first layer and the layer immediately above the infill.

### The dilemma

High temperature = stringing.
Low temperature = ripping.

### The solution

- Retraction, fan speed, and coasting were the main solutions for stringing.
- `Gyroid` pattern for infill prevented the nozzle from scraping/accumulating goo when crossing freshly laid infill. Unlike most other patterns, Gyroid infill lines never cross themselves.
- Reducing `Top/Bottom Speed` addressed ripping long lines. Sadly, this speed decrease took effect over ALL top-bottom lines, not just the first layers, but overall, the time cost of that was minor.
- When stringing was gone, whiskers at each layer's start point became visible. This was addressed by increasing retraction distance from `1.8 mm` to `3 mm` (2mm or 2.5mm were not tested though, could work just as well).

### Final Cura settings

| Setting | Value |
| --- | --- |
| Infill Pattern | Gyroid |
| Printing Temperature | `220 C` |
| Printing Temperature Initial Layer | `240 C` |
| Top/Bottom Speed | `70 mm/s` |
| Initial Layer Speed | `15 mm/s` |
| Retraction Distance | `3 mm` |
| Fan Speed | `30%` |
| Maximum Fan Speed | `50%` |
| Enable Coasting | `true` |
