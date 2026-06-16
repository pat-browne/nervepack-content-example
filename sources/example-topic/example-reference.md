---
name: example-reference
source_url: https://example.com/docs/some-spec
version: "1.0 (2026-01-01)"
captured_date: 2026-06-16
scope: "The 'Configuration' and 'CLI flags' sections only — the surface we actually consult."
license: "CC-BY-4.0 (replace with the upstream's real license)"
topic: example-topic
kind: reference
---

# EXAMPLE: a curated source

> **Template.** A `sources/<topic>/<name>.md` file is a *durable, version-pinned*
> technical reference trimmed to the scope you actually consult — official docs, a
> spec, an RFC, a language book chapter. Not blog posts, not "10 best practices"
> listicles, not Stack Overflow answers. The frontmatter above is required: it records
> exactly which version you captured so the agent knows when it's gone stale.

## Why a source and not just context7

`sources/` is for things you consult **repeatedly** and want to **annotate and
cross-link** in the wiki layer. For one-off "what's the latest API right now" lookups,
use context7 instead — don't mirror a whole doc tree here.

## The consulted surface

`<paste or summarize only the chapters/sections/APIs named in the frontmatter `scope`.
Pointers + targeted excerpts beat full mirrors every time.>`

- `<key fact / API signature / config option you actually use>`
- `<another>`

## Cross-links

A source earns its place by being referenced. Link it from a wiki synthesis page
(`wiki/entities/<topic>.md`) so it isn't an orphan — see [[example-entity]].
