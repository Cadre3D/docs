---
title: "Export and interop"
description: "Export to STL, OBJ, STEP, 3MF, and glTF/GLB from the exact model, plus a scripting surface and review JSON for automation."
---

# Export & interop

Cadre exports to standard formats so your geometry is never locked inside the
tool. Every export is generated from the exact model the kernel holds.

## Geometry formats

| Format | What it faithfully preserves |
|---|---|
| **STL** (binary / ASCII) | The model's triangle mesh. The universal 3D-print format. |
| **OBJ** | The triangle mesh with per-object structure. |
| **3MF** | The triangle mesh in the modern print container format. |
| **glTF / GLB** | The triangle mesh for viewing and real-time rendering. |
| **STEP** | Analytic surfaces (planes, cylinders, cones, spheres, tori) for the shapes that support them, plus a mesh fallback where they do not. |

STL, OBJ, 3MF, and glTF/GLB are triangle meshes: a curved surface is
approximated by facets. STEP is different — for supported solids it carries the
true curved surface, so a cylinder exports as a cylinder, not a ring of flat
faces.

### What STEP does and does not claim

STEP export emits exact analytic faces for primitives, their transforms, and
their boolean combinations where those surfaces are supported. It is faithful for
that geometry. It is not a full parametric-history transfer: the feature tree and
editing intent do not travel in the file — the resulting solid does.

## Import

Import STL and OBJ files. On import, duplicate vertices are auto-welded and you
get a report: triangle count, welded duplicates, open edges, and degenerate
faces. The open-edge count tells you whether an imported mesh is watertight
before you build on it.

## Share a review

- **Review link** — share a read-only link to a review. The recipient sees the
  flags and suggestions alongside the model, and clicking a flag frames the part
  it points to — no editor or account needed.
- **Review JSON** — export any review as structured JSON for downstream tools and
  agents. The same review is also available as Markdown or a printable page.

## Automation

A stable in-browser scripting surface (`window.cadre`) drives the editor from a
script or CI — build solids, then export — so modeling can run headlessly, not
only by clicking. For example: `await cadre.ready()`, `cadre.addBox()`,
`cadre.exportStl()`.

## The interop principle

Because every export comes from the one geometry authority
(see **[Architecture](../architecture.md)**), what leaves Cadre matches what the
kernel measured. Re-import an exported file and confirm it for yourself — the
measurements agree.
