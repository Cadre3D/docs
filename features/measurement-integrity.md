---
title: "Measurement integrity"
description: "Volume, surface area, and watertightness computed from the geometry as trust properties, not screen estimates."
---

# Measurement integrity

Numbers are only useful if you can trust them. In Cadre, volume, surface area,
and watertightness are computed from the model's geometry by the same kernel that
builds it — not estimated on screen. That is a trust property, not a convenience
feature.

## What is measured

- **Volume and surface area** — computed directly from the model's geometry:
  exactly for a flat-faced solid, and to tessellation resolution for a curved
  surface. Build a 10 mm cube and read 1000 mm³ and 600 mm².
- **Bounding dimensions** — the model's extent along each axis.
- **Watertightness** — whether the solid is closed and manifold, reported live in
  the Property panel as a watertight / open-edge readout.
- **Overhang** — a toggleable heatmap that tints each surface by its build-angle
  severity for FDM, so you can see where a print will need support.
- **Point-to-point distance** — an interactive measure tool in the viewport.

## Why it is a trust property

There is only one geometry engine (see **[Architecture](../architecture.md)**),
so the measurement you read, the flag the [AI reviewer](ai-review.md) cites, and
the file you [export](export-interop.md) all come from the same source. They
cannot quietly disagree.

This is also what keeps AI review honest: a measured flag has to carry a real
number from this layer, and a flag the measurement does not support is dropped.
The measurement is the anti-guessing floor under every claim Cadre makes.

## Watertightness and booleans

Because watertightness is measured, Cadre can refuse to produce a broken solid: a
boolean operation that would yield a non-watertight or non-manifold result is
rejected with an explanation rather than baked in. An imported mesh that is not
watertight is flagged by its open-edge count on import, so you know before you
build on it.

## Honest precision

Volume, surface area, and watertightness are computed from the model's triangles —
exact for a flat-faced solid, and accurate to the tessellation for a curved one; a
STEP export additionally carries the true curved surface. Interactive
manufacturability metrics such as wall thickness and overhang angle are sampled
from the surface: measured from the model, not guessed on screen, at sampling
resolution rather than analytically perfect. Cadre states the number and the
threshold so you can always check it yourself.
