---
title: "Architecture"
description: "How Cadre stays trustworthy: one geometry authority, one review pipeline, and verified export, described as properties rather than internals."
---

# Architecture

Cadre's trustworthiness comes from three architectural properties. This page
describes what they guarantee, not how they are implemented.

## 1. One geometry authority

All geometry — vertices, faces, transforms, boolean results, measurements — is
computed by a single kernel written in Rust and compiled to WebAssembly, running
locally in your browser. The interface layer holds identifiers, transforms, and
display buffers, and never edits geometry itself.

The guarantee: every number you see (a volume, a wall thickness, an overhang
angle) is produced by the same kernel that builds the model. There is no second,
approximate geometry engine on screen that could disagree with the exported
file.

## 2. One review pipeline

AI review and human review are not separate systems. A flagged issue, a proposed
parameter change from the AI, and a suggestion from a collaborator all arrive
through the same review inbox and are applied — or discarded — through the same
path. An accepted change lands as one reversible step in the model's history.

The guarantee: an AI suggestion is held to the same accept/discard discipline as
a human one. Nothing is applied to your model automatically; you are always the
one who accepts.

## 3. Verified export

Exports are generated from the exact model the kernel holds, not from a separate
copy or a screen snapshot. Mesh formats carry the model's triangles; the analytic
STEP export carries true curved surfaces for the shapes that support them.

The guarantee: what you export is what the kernel measured. You can re-import an
exported file and confirm it matches.

## Why in the browser

Running the kernel as WebAssembly keeps modeling, boolean operations, and
measurement local and deterministic: the same input produces the same geometry
and the same numbers on every machine, with no round trip to a server. An
optional cloud backend adds accounts, cloud save, and collaboration, but every
modeling and measurement operation works without it.

See **[Methodology](methodology.md)** for how to verify each of these properties
yourself.
