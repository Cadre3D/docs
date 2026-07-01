---
title: "AI review"
description: "AI manufacturability review grounded in the kernel's measured geometry (thin walls, overhangs, enclosed voids) with concrete parameter fixes."
---

# AI review

Cadre's AI reviewer reads your actual model — the geometry the kernel holds, not
a screenshot — and flags the things that ruin a print, grounding the measurable
ones in a checkable number and proposing a concrete fix.

## Manufacturability flags

The reviewer surfaces issues as clickable markers that frame the problem in the
viewport:

- **Thin walls** — a wall too thin to survive the process.
- **Steep overhangs** — surfaces that will sag or need support in FDM.
- **Sharp internal corners** — stress risers and hard-to-machine features.
- **Small features** — details below what the process can hold.
- **Enclosed voids** — sealed internal cavities that would trap uncured resin or
  unfused powder and cannot drain.
- **Non-watertight solids** — non-manifold geometry that will not print cleanly.

## Grounded in measured geometry

This is the property that separates Cadre from a screenshot reviewer. A flag of a
measured kind — thin wall, overhang, enclosed void, non-watertight solid — must
cite the kernel's own measured value. If the measurement does not support the
flag, the flag is dropped before it reaches you.

So a thin-wall flag reads "wall 0.8 mm, threshold 2.0 mm" — a number you can
check against a caliper — not a vague "looks thin." See
**[Methodology](../methodology.md)** for how to verify this yourself.

## Parameter fixes

For a part you modeled in Cadre, the reviewer proposes the fix as a typed
parameter change shown as `old → new` (for example, "wall 0.8 → 2.1 mm"). Accept
it and it applies as a single reversible edit through the
**[review inbox](review-inbox.md)**. For an imported mesh with no feature tree,
you still get the measured flag and the number to fix by hand.

## Process presets

Choose a material and process — FDM, SLA, machined, or sheet metal — and the
relevant checks and thresholds apply. A thin wall for one process is fine for
another; the presets keep the flags honest to how you will make the part.

## Honest scope

The reviewer explains, prioritizes, and suggests. Detection and grounding are
done by the kernel; the AI turns measured numbers into plain-language flags and
parameter suggestions. It is not a generate-a-part-from-text tool, and it never
edits your model on its own — it proposes, and you accept.
