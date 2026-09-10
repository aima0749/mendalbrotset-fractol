# Colorful Mandelbrot Set Fractal 🌀

A Python script that generates a vibrant, multi-colored visualization of the
**Mandelbrot set** — one of the most famous fractals in mathematics — using
only `numpy` and `matplotlib`.

<img width="800" alt="Mandelbrot Set Preview" src="https://github.com/user-attachments/assets/d7dba2d0-64f1-4b62-b866-1bc75ebd0ff3">

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

```text
Z(n+1) = Z(n)^2 + C
