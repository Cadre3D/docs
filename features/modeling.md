---
title: "Modeling"
description: "Sketch, parametric primitives, an editable feature tree, booleans, variables, and transforms. Parts that stay editable."
---

# Modeling

Cadre is a parametric modeler: shapes stay editable, and every part is described
by parameters you can change at any time.

## Sketch

Draw 2D profiles on the standard planes or on a selected face of an existing
solid. Tools include line, polyline, rectangle, circle, arc, polygon, and a 2D
fillet, with snapping to faces, edges, and vertices. Closed loops are detected
automatically as profiles ready to turn into solids.

## Primitives

Eight parametric primitives — box, cylinder, sphere, cone, torus, wedge, pyramid,
and tube. Each stays re-editable from the property panel: change a dimension and
the shape updates.

## Feature operations

- **Extrude** a profile — one side or mid-plane, to a distance, through all, or
  up to a chosen face or vertex.
- **Revolve** a profile from 0 to 360 degrees.
- **Fillet & chamfer** — a constant-radius round that follows tangent edges
  automatically, or a straight bevel, from the same edge selection.

## Boolean operations

Union, subtract, and intersect combine solids into a sound, watertight
body. In the rare case a combination would produce a non-watertight or
non-manifold result, it is refused with an explanation rather than baked into a
broken body — so what you keep building on stays sound.

## Feature tree

Every operation is a node in an editable feature tree. Click a feature to edit
it; roll the build marker back to an earlier state; suppress and unsuppress
features; the model recomputes down the tree. Changes are re-editable, not
one-way.

## Variables & expressions

Name your dimensions and drive parameters with expressions like `width / 2` or
`2 * thickness + 1`. A circular reference is caught before any change is applied.

## Transforms & patterns

Move, rotate, and scale with a gizmo and per-axis lock. Mirror a body, or repeat
it as a linear or circular array.

## Selection & history

Select by object, face, edge, or vertex, with multi-select. Identifiers stay
stable through transforms and boolean operations, so a combined body remains
filletable, snappable, and sketchable on its new faces. Every change is undoable
through a deep, clickable history timeline.

Modeling in Cadre feeds **[AI review](ai-review.md)**: the richer the parametric
model, the more a suggested fix can be a single parameter change.
