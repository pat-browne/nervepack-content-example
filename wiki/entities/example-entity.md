---
name: example-entity
kind: entity
last_updated: 2026-06-16
sources: ["example-reference"]
---

# EXAMPLE: a wiki entity page

> **Template.** A wiki *entity* page synthesizes what you know about a **thing** —
> a tool, a service, a language, a system you own (`rust`, `aws`, `playwright`,
> `acme-widget`). It draws across your skills and sources and ties them together.
> Concepts (ideas like `prompt-caching`) go in `wiki/concepts/` instead.

## What this is

`<2–4 sentences orienting the reader to the entity: what it is, why you care, how it
fits your work.>`

## What we know

- `<a synthesized fact, citing where it comes from>` — see [[example-reference]].
- `<another, linking a skill>` — see [[np-kb-example-infra-pointer]].

## Open questions / gaps

`<things you haven't pinned down yet — dangling [[links]] here are fine; they mark
future work.>`

---

A wiki page is regenerated (or surgically updated) when a new source is ingested on
the same topic, when a skill it cross-links changes materially, or when the lint pass
flags it stale. Cite both skills (`[[skill-name]]`) and sources (`[[source-name]]`).
