---
title: "Trust and data"
description: "No install, offline-capable, local-first, and open formats in and out. How Cadre keeps your models yours."
---

# Trust & data

## No install, any modern browser

Cadre is a web application. There is nothing to download or update: open the page
and model. It runs on current desktop browsers with WebAssembly support.

## Offline-capable

The editor works fully offline. Modeling, boolean operations, measurement,
import, and export all run locally in your browser with no network connection.
The app installs as a Progressive Web App and caches itself for offline use.

Features that inherently need a network — accounts, cloud save,
collaboration, and AI review — are the only ones that require connectivity. When
no cloud backend is configured, those surfaces are simply absent, and everything
else still works.

## Local-first, your model stays yours

Your work autosaves locally in your browser and restores when you reopen the tab.
A model stays on your machine unless you deliberately save it to the cloud or
share a link. Cadre does not require an account to model, measure, or export.

- **Your models are never uploaded implicitly.** Saving to the cloud and sharing
  a review link are explicit, opt-in actions. When a cloud backend is configured,
  Cadre does send usage statistics and error reports to keep the service
  reliable — anonymous when you are signed out, tied to your account when you
  are signed in. These never include your model geometry.
- **Your files are open formats.** What you import and export are standard files
  you can open in other tools, so your geometry is never locked inside Cadre.

## Formats & interop

| Direction | Formats |
|---|---|
| **Import** | STL (binary and ASCII), OBJ — auto-welded, with an open-edge report |
| **Export** | STL, OBJ, STEP (analytic surfaces), 3MF, glTF/GLB |
| **Share**  | A review link, and a structured JSON export of any review for downstream tools |

STL, OBJ, 3MF, and glTF/GLB are triangle meshes. STEP export additionally carries
true curved surfaces for the shapes that support them, so a cylinder exports as a
cylinder rather than a facet approximation. See
**[Export & interop](features/export-interop.md)** for what each format
preserves.

## Data ownership, as a principle

You own your models. Cadre is a place to make and review them, not a vault that
holds them hostage: every model can leave as an open file, and your geometry
never leaves your browser unless you send it.
