---
title: "Methodology"
description: "Why Cadre's outputs are trustworthy, and how you can verify each claim yourself, from measured volume to geometry-grounded AI flags."
---

# Methodology — trust, and how to check it

Cadre makes a small number of concrete claims. Each one is verifiable by you,
without taking our word for it. This page gives the claim and the check; it does
not describe the internal algorithms that produce the result.

## Claim: measurements come from the geometry, not a guess

Volume, surface area, and bounding dimensions are computed from the model the
kernel holds.

**Check it.** Build a 10 mm cube. The Property panel reports a volume of
1000 mm³ and a surface area of 600 mm². Scale or combine shapes and the numbers
track the geometry exactly.

## Claim: AI flags are grounded in measured values

An AI manufacturability flag of a measured kind — thin wall, overhang, enclosed
void, non-watertight solid — must cite the kernel's own measured number. A flag
the measurement does not support is dropped before you ever see it.

**Check it.** Open a review and read any measured flag: it states the value and
the threshold (for example, "wall 0.8 mm, threshold 2.0 mm"). Export the review
as JSON and confirm each measured flag carries its number. Print the part and a
caliper agrees with the reported wall.

## Claim: an accepted fix is one reversible change

For a part with a feature tree, an accepted parameter suggestion applies as a
single typed edit (`old → new`) and a single history entry.

**Check it.** Accept a suggestion, read the one-line history entry it created,
then undo it and watch the model return exactly to its previous state.

## Claim: exports match the model

An exported file is generated from the exact geometry the kernel measured.

**Check it.** Export to STL or OBJ, re-import the file, and compare the
measurements. Volume and surface area match within the format's representation.

## What we deliberately do not claim

- Interactive metrics like wall thickness and overhang are sampled from the
  surface, not analytically perfect; they are measured, not estimated on screen,
  which is the property that matters for a trustworthy flag.
- Collaboration is presence and asynchronous suggestions, not live simultaneous
  co-editing. See **[Collaboration](features/collaboration.md)**.
