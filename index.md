---
title: "Cadre Documentation"
description: "Cadre is an AI co-reviewer for parametric CAD in the browser: model parts, catch manufacturability issues grounded in measured geometry, and export to STL, OBJ, STEP, 3MF, and glTF/GLB."
---

# Cadre Documentation

**AI co-reviewer for parametric CAD.** Model parts in the browser, then have AI
flag manufacturability issues — thin walls, sharp internal corners, steep
overhangs, small features, enclosed voids, non-watertight solids — and propose
concrete parameter changes. AI suggestions and human suggestions arrive in one
review inbox; you accept or discard each with one click.

Cadre runs in any modern browser with no install. Geometry is computed by a
Rust/WebAssembly kernel and measured from the model itself, not estimated on
screen.

> **Try it now — nothing to install:** [cadre3d.com](https://cadre3d.com/)

## What Cadre does

- **[Modeling](features/modeling.md)** — sketch, parametric primitives, and an
  editable feature tree with variables and expressions.
- **[Review inbox](features/review-inbox.md)** — one queue for AI and human
  suggestions, each accepted or discarded as a single reversible step.
- **[AI review](features/ai-review.md)** — the measurable flags (thin wall,
  overhang, enclosed void, watertightness) grounded in the kernel's own measured
  number, with parameter fixes shown as `old → new`; sharp corners and small
  features are the reviewer's inferred judgment call.
- **[Collaboration](features/collaboration.md)** — presence, link sharing, and
  asynchronous fork-and-suggest review.
- **[Export & interop](features/export-interop.md)** — STL, OBJ, 3MF, and
  glTF/GLB meshes out, plus STEP with true analytic surfaces (a cylinder exports
  as a cylinder, not a faceted shell); a shareable review link; a structured
  JSON review for tools.
- **[Measurement integrity](features/measurement-integrity.md)** — volume,
  surface area, and watertightness computed from the geometry as trust
  properties.

## How it works, and why to trust it

- **[Architecture](architecture.md)** — the three properties that make outputs
  trustworthy: one geometry authority, one review pipeline, verified export.
- **[Methodology](methodology.md)** — the claims Cadre makes, and how you can
  check each one yourself.
- **[Trust & data](trust.md)** — no-install, offline-capable, local-first, and
  what stays on your machine.
