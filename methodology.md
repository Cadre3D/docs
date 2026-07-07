---
title: "Methodology"
description: "Why Cadre's outputs are trustworthy, and how you can verify each claim yourself, from measured volume to geometry-grounded AI flags."
---

# Methodology — trust, and how to check it

Cadre makes a small number of concrete claims. Each one is verifiable by you,
without taking our word for it. This page gives the claim and the check.

## Claim: measurements come from the geometry, not a guess

Volume, surface area, and bounding dimensions are computed from the model
itself.

**Check it.** Build a 10 mm cube. The Property panel reports a volume of
1000 mm³ and a surface area of 600 mm². Scale or combine shapes and the numbers
track the geometry.

## Claim: AI flags are grounded in measured values

An AI manufacturability flag of a measured kind — thin wall, overhang, enclosed
void, non-watertight solid — must cite the kernel's own measured number. A flag
the measurement does not support is dropped before you see it.

**Check it.** Open a review and read any measured flag: it states the value and
the threshold (for example, "wall 0.8 mm, threshold 2.0 mm"). Export the review
as JSON and confirm each flag carries its number.

## Claim: an accepted fix is one reversible change

For a part with a feature tree, an accepted parameter suggestion applies as one
typed edit (`old → new`) and one history entry.

**Check it.** Accept a suggestion, read the one-line history entry it created,
then undo it and watch the model revert.

## Claim: exports match the model

A mesh export (STL, OBJ, 3MF, GLB) comes from the exact geometry the kernel
measured; volume and surface area match within the format's mesh representation.
A STEP export goes further: for the geometry Cadre authored — primitives,
transforms, and their boolean combinations — it carries exact analytic surfaces,
so a re-imported cylinder returns as a true cylinder of the exact radius, its
volume and area round-tripping exactly. A curved surface that can't be
represented exactly exports as a faithful mesh.

**Check it (mesh).** Export to STL or OBJ, re-import, and compare the
measurements.

**Check it (STEP).** Bore a hole through a box, export to STEP, and re-import:
the bore returns as a true cylindrical face, volume matching.

## What we deliberately do not claim

- Interactive metrics like wall thickness and overhang are sampled, not
  analytically perfect; they are measured, not estimated on screen — the property
  that matters for a trustworthy flag.
- Collaboration is presence and asynchronous suggestions, not live simultaneous
  co-editing. See **[Collaboration](features/collaboration.md)**.
