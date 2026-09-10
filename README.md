# Colorful Mandelbrot Set Fractal 🌀

A Python script that generates a vibrant, multi-colored visualization of the
**Mandelbrot set** — one of the most famous fractals in mathematics — using
only `numpy` and `matplotlib`.

![Mandelbrot Set Preview](mandelbrot.png)

## The Beauty of the Mandelbrot Set

What makes the Mandelbrot set so captivating is that a single, almost
absurdly simple equation — `Z(n+1) = Z(n)^2 + C` — unfolds into a shape of
endless, breathtaking complexity. There is no template, no artist's hand
guiding the outline; every swirl, spiral, and spike emerges purely from
arithmetic repeated millions of times.

A few things make it genuinely beautiful:

- **Infinite detail.** No matter how far you zoom into the boundary, new
  structure keeps appearing — tendrils, spirals, and seahorse-like curls
  that never resolve into a simple line. The coastline just keeps getting
  more intricate the closer you look.
- **Self-similarity with variation.** Miniature copies of the whole
  Mandelbrot set appear scattered throughout its own boundary, but each one
  is subtly warped and dressed in different filigree — an echo of the whole,
  never an exact repeat.
- **Order at the edge of chaos.** The interior (points that never escape)
  is calm and solid, while the exterior explodes outward smoothly. All the
  drama, complexity, and color happens in the razor-thin boundary between
  the two — a perfect visual metaphor for the line between stability and
  chaos.
- **Color as a window into speed, not just position.** The vivid rings in
  this rendering aren't decoration for its own sake — they encode *how fast*
  each point escapes to infinity. The color you see is really a map of
  mathematical behavior, which is part of why it feels so alive.
- **Democratized wonder.** Anyone with a laptop and a few lines of code can
  rediscover something this intricate. It's one of the clearest examples of
  how deep beauty can come from deep simplicity.

## Overview

The Mandelbrot set is defined by iterating the recurrence relation:

```
Z(n+1) = Z(n)^2 + C
```

for a complex number `C`, starting at `Z(0) = 0`. A point `C` belongs to the
set if this sequence stays bounded (never escapes to infinity) no matter how
many times it's iterated. Points that *do* escape are colored based on **how
fast** they escape, which is what produces the intricate, colorful bands
around the set's boundary.

This project renders that boundary with a custom vivid, cyclic color palette
so the same set of colors repeats several times outward from the fractal
edge, producing a highly saturated, "glowing" look rather than a single
smooth gradient.

## Features

- Fractal computed from scratch with vectorized NumPy (no external fractal
  libraries).
- Smooth escape-time coloring for clean, non-banded edges at the boundary.
- Custom cyclic color map (magenta → purple → blue → cyan → green → yellow →
  orange → red) for a vibrant, repeating rainbow effect.
- Fully configurable: zoom region, iteration depth, resolution, color count,
  and palette are all simple variables at the top of the function.

## Requirements

- Python 3.8+
- `numpy`
- `matplotlib`

Install dependencies:

```bash
pip install numpy matplotlib
```

## Usage

Run the script directly:

```bash
python3 mandelbrot.py
```

This generates `mandelbrot.png` in the same directory.

## Customization

All the knobs you'd want to turn live in `make_design()` and `mandelbrot()`:

| Variable | What it does |
|---|---|
| `size` | Output resolution (pixels per side) |
| `max_iter` | Max iterations before a point is considered "in the set" — higher gives finer detail at the boundary |
| `x_min, x_max, y_min, y_max` | The region of the complex plane to render — change these to zoom into a different part of the fractal |
| `vivid_colors` | The list of hex colors used in the cyclic palette |
| `cycles` | How many times the palette repeats across the escape-time range — higher = more, tighter color bands |

**Example — zoom into the "seahorse valley":**

```python
div_time = mandelbrot(size, -0.8, -0.7, 0.05, 0.15, max_iter=500)
```

## How It Works

1. A grid of complex numbers `C` is built over the chosen region of the
   complex plane.
2. Each point is iterated through `Z = Z^2 + C` up to `max_iter` times.
3. A boolean mask tracks which points have "escaped" (i.e. `|Z| > 2`); once a
   point escapes, it's no longer updated.
4. A **smooth coloring formula** (based on the log of the escape magnitude)
   assigns each escaped point a continuous value instead of a raw iteration
   count, avoiding harsh color bands.
5. That value is wrapped (`% `) into a small number of cycles and mapped
   through a custom `LinearSegmentedColormap` to get the repeating, vivid
   color rings.
6. Points that never escape (the interior of the set) are colored solid
   black for contrast.

## Project Structure

```
.
├── mandelbrot.py     # Main script
├── mandelbrot.png    # Example output
└── README.md
```

## Author

- **Name:** _<your name>_
- **Course:** BS (Computer Science) — Design Lab 01: Designing Using Fractals

## License

This project is released for educational purposes. Feel free to fork, modify,
and experiment with different regions, palettes, and iteration depths.
