---
title: "Review inbox"
description: "One review inbox for AI and human suggestions, each accepted or discarded as a single reversible step."
---

# Review inbox

The review inbox is the one place suggestions land — whether they come from the
AI reviewer or from a human collaborator. Both flow through the same queue and
the same accept/discard controls.

## One queue, two sources

- **AI suggestions** arrive from the [AI reviewer](ai-review.md): a
  manufacturability flag, and often a proposed parameter change to fix it.
- **Human suggestions** arrive from a [collaborator](collaboration.md) who forked
  your shared model, made an edit, and submitted it back.

They sit side by side, each labeled by source. Nothing distinguishes them
procedurally: an AI suggestion is reviewed the same way a teammate's is.

## What a suggestion shows

- **The flag or intent** — what the change addresses, framed against the actual
  model.
- **The concrete change** — for a parametric part, a typed parameter edit shown
  as `old → new`.
- **A visual diff** — for a human suggestion, the differences are highlighted:
  added, modified, removed, moved, renamed, or resized.

Click a flagged issue and the camera frames it in the viewport, so you see the
problem before you decide.

## Accept or discard

Every suggestion is resolved by you, with one click:

- **Accept** applies the change. For a parametric part, it lands as a single,
  reversible history entry — one line you can read and undo.
- **Discard** dismisses it without touching your model.

Nothing is applied automatically. The AI proposes; a human accepts. This is the
discipline that makes an automated reviewer safe to keep on: it can only ever
suggest, never edit.

## Why one pipeline matters

Because AI and human review share the same rails, a suggestion behaves
identically no matter who made it. There is no separate, less-careful path for
machine edits, and adding review from people is a natural extension of the same
mechanic rather than a second system to trust.
