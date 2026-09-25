# Citrus Mosaic

**A seed-based generative system for arc-and-triangle tile mosaics.**

A catalogue of computational textile compositions for fashion, textile and surface design — algorithmically drawn, seed-documented, and ready for production.

---

## Overview

Citrus Mosaic is a generative design system rather than a single artwork. Each composition is built from a square grid of tiles, each tile drawn from one of twenty-two possible arc, triangle, or split variants — coloured from a citrus palette of blues, greens, and warm yellows. Where the tiles meet, a mosaic emerges.

The system is designed for:

- **Fashion houses** adapting tiled ornament for apparel and accessories
- **Textile studios** developing repeat patterns and yardage
- **Surface designers** working across print, wallpaper, and interior applications

Every composition can be licensed, adapted, or commissioned to a brief.

---

## Concept

A tile, when it is *repeated* across a grid, becomes a mosaic — citrus, structural, quietly yours.

The tiled surface — repeated, rule-bound, endlessly variable — has always carried meaning. From ceramic tilework to textile block-prints, the repeated square is the oldest system of decorative computation we have. Citrus Mosaic translates that structure into code. Each composition begins with a small grid and unfolds through per-tile variation until the frame fills with an intricate, citrus-coloured mosaic.

The palette, the grid division, and the per-tile pattern are all derived from a single numeric seed.

Like the other still volumes in this series (Girih, Arachne, Celestial Grove, ChaotiColor), **Citrus Mosaic is a static composition.** The plate, the framed plate, the surfaces, and the archive are all static frames. A mosaic is something you stand in front of; its character is stillness, not motion.

---

## Features

- **Seed-based generation** — every composition is defined by a numeric seed and can be regenerated exactly
- **Deterministic output** — the same seed always produces the same composition
- **Twenty-two tile variants** — arcs, triangles, splits, and full-fill patterns
- **Citrus palette** — a range of blues, greens, and warm yellows
- **Soft glow** — each tile carries a subtle glow that ties the mosaic together
- **Adaptive grid** — 2 to 14 divisions per axis, derived from the seed
- **Adaptive surfaces** — one seed applied across print, scarf, textile, and wall formats
- **Archive** — eight curated seeds available for immediate loading
- **Download** — export the composition as a high-resolution PNG
- **Keyboard shortcuts** — `R` for new seed, `S` to save

---

## Project Structure

```
.
├── index.html          # Main catalogue page
├── images/
│   ├── fav.svg         # Favicon
│   ├── tote.png        # Mockup: tote bag
│   ├── tee.png         # Mockup: t-shirt
│   └── cushion.png     # Mockup: cushion
└── README.md
```

---

## How It Works

### The Seed

A numeric seed (a large integer) initializes a deterministic pseudo-random generator. From this seed, the system derives:

- Background glow colour (from a palette of 22 tones)
- Grid division count (2–14)
- Per-tile colour (from a palette of 27 squares)
- Per-tile pattern variant (0–21)

Because the generator is deterministic, the same seed always produces the same composition — on any device, at any time.

### The Tiles

Each tile is drawn into its own cell of the grid, using one of twenty-two variants. The variants fall into four families:

| Family       | Variants | Description                                        |
|--------------|----------|----------------------------------------------------|
| Quarter arcs | 0–3      | A quarter-circle arc anchored to one corner        |
| Triangles    | 4–7, 12–15 | Triangular fills connecting three corners or edges |
| Split tiles  | 8–11, 16–19 | Half-circles or half-rectangles along one edge   |
| Full fills   | 20–21    | Full-tile rectangle fills                          |

Each variant is drawn with a subtle glow — a shadow blur equal to half the tile width — that softens the edges and ties the mosaic together.

### The Grid

The grid division count is derived from the seed, between 2 and 14 on each axis. This means each composition has its own density:

- A **coarse grid** (2×2 or 3×3) produces large, bold tiles.
- A **fine grid** (12×12 or 14×14) produces intricate, textile-like detail.

The total square count is `divisions × divisions`, so a 14×14 grid contains 196 individually-coloured tiles.

### The Palette

Two colour systems meet in every composition:

- **Square colours** — the fill of each tile, drawn from a palette of 27 vivid hues: cyan, green, yellow, orange, red, magenta, and violet.
- **Foreground colour** — the tile pattern's arc/triangle colour, drawn from a palette of 22 citrus tones: whites, blues, sea greens, and warm accents.

Where the two meet, the mosaic reads as a bright, layered field.

### The Surfaces

The same seed is rendered across four surface formats. These are static frames — they represent the print-ready composition.

| Surface  | Aspect | Material          |
|----------|--------|-------------------|
| Print    | 1 : 1  | Cotton rag        |
| Scarf    | 3 : 1  | Twill silk        |
| Textile  | 4 : 3  | Fabric yardage    |
| Wall     | 2 : 3  | Wallpaper         |

Each surface uses the same underlying seed and structural logic — only the repeat, orientation, and scale change.

### Stillness

Like Girih, Arachne, Celestial Grove, and ChaotiColor, Citrus Mosaic does not animate. The plate is a single frozen frame — the composition is complete the moment it is generated.

This is a deliberate design choice. A mosaic is not a swarm. It is not a rotation. It is a grid of tiles, laid down and fixed. Its stillness is what makes it print-ready in the strictest sense: what you see is what you get.

---

## Usage

### In the browser

1. Open `index.html` in any modern browser.
2. Click **New Seed** to generate a new composition.
3. Click **Download** to save the composition as a PNG.
4. Scroll to the **Archive** section and click any plate to load it into Plate 001.

### Keyboard shortcuts

| Key | Action          |
|-----|-----------------|
| `R` | New seed        |
| `S` | Save as PNG     |

### Reproducing a composition

Each composition is identified by an 8-digit seed label displayed in the metadata panel. To reproduce a specific composition, note the seed and regenerate it programmatically:

```js
const rng = new RandomGenerator(seed);
const features = buildFeatures(rng);
renderComposition(canvas, features, rng);
```

Because the generator is deterministic, this will produce the identical composition on any device.

---

## Technical Notes

- **No build step.** The system is a single HTML file with inline CSS and JavaScript.
- **No dependencies.** All drawing is done with the native Canvas 2D API.
- **Deterministic.** The `RandomGenerator` class uses a xorshift-based PRNG seeded by an integer, so identical seeds produce identical outputs.
- **Static rendering.** Every canvas renders a single frame. There is no animation loop.
- **Feature isolation.** Cover, framed plate, surfaces, and archive thumbnails each derive their own feature set from their own local RNG, without disturbing the main plate's state.
- **Complete variant coverage.** All 22 tile variants (0–21) are handled; no value falls through.
- **Responsive.** The layout adapts from large desktop down to very small mobile devices (tested at 360px viewport width).
- **Accessible.** Supports `prefers-reduced-motion`. Pinch-zoom is enabled.

### Browser support

Tested in current versions of:

- Chrome / Edge
- Firefox
- Safari (desktop and iOS)

---

## Licensing

All Citrus Mosaic compositions are **seed-documented** and available for licensing across textile, surface, and print applications.

- **Standard licenses** cover single-product production runs.
- **Commercial use, custom editions, or exclusive rights** are available on request.

Each license is issued against a specific seed ID. Regeneration of the same seed produces the identical composition — ensuring reproducibility between artist, studio, and manufacturer.

For licensing enquiries: [reyhanehdaneshdoost@gmail.com](mailto:reyhanehdaneshdoost@gmail.com)

---

## Commission

Citrus Mosaic is a generative design system, not a fixed artwork. It can be adapted for specific briefs:

| Service     | Description                                                       |
|-------------|-------------------------------------------------------------------|
| Licensing   | Existing seeds from the archive, licensed for production use      |
| Commission  | New compositions designed to your palette, repeat, and product    |
| Systems     | A private generative tool built for your studio's ongoing use     |

To begin a conversation: [reyhanehdaneshdoost@gmail.com](mailto:reyhanehdaneshdoost@gmail.com)

---

## Series

Citrus Mosaic is part of a computational textile series. Each volume approaches ornament from a different structural angle:

| Volume             | Structure                    | Motion                     |
|--------------------|------------------------------|----------------------------|
| Girih 1            | Islamic geometric            | Static                     |
| Arachne            | Rotating rings               | Static                     |
| Baroque Me Baby    | Baroque frames               | Static                     |
| Bezier 1           | Concentric curves            | Static                     |
| Bezier 2           | Single rotating curve        | Animated (plate)           |
| Brownian Graphe    | Graph networks               | Animated + interactive     |
| Celestial Grove    | Recursive branch trees       | Static                     |
| ChaotiColor        | Cellular automata            | Static                     |
| **Citrus Mosaic**  | **Arc-and-triangle tiles**   | **Static**                 |

The series is designed as a coherent whole — same page structure, same seed logic, same licensing and commission terms — so that each volume can be presented individually or as part of a larger body of work.

---

## Credits

- **Design & Generative System** — Reyhaneh Daneshdoost
- **Typefaces** — Cormorant Garamond · DM Mono
- **Platform** — Reyrove Studio
- **Edition** — Citrus Mosaic, Autumn 2026

### On AI tools

Where technical obstacles were encountered, AI tools were used for debugging and code optimization. Every structural, aesthetic, and conceptual decision remained the artist's own.

---

## Links

- Website — [reyrove.github.io](https://reyrove.github.io/)
- Instagram — [@rey._.rove](https://www.instagram.com/rey._.rove/)
- LinkedIn — [Reyhaneh Daneshdoost](https://www.linkedin.com/in/reyhaneh-daneshdoost-730481160/)
- X — [@reyrove](https://x.com/reyrove)

---

© Citrus Mosaic · All compositions reproducible by seed · Computational Textile Design