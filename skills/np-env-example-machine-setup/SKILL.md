---
name: np-env-example-machine-setup
description: TEMPLATE — copy into your content overlay and rename. Records your machine/environment choices (editor extensions, CLI tools, plugin stack, shell config) so a fresh box reproduces your setup and the agent knows what's installed. Use when bringing up a new machine or hitting a missing-tool error.
---

# EXAMPLE: an environment-setup skill

> **Template, not a live skill.** Copy into `$NP_CONTENT_DIR/skills/`, rename to
> `np-env-<topic>`, fill in your real choices. Replace every `<…>`.

`np-env-` skills capture *your* environment decisions — the curated list you'd want
re-applied on every machine, and that the agent should assume is present.

## What you install / configure

- **<category, e.g. editor extensions>:** `<id>` — `<one-line why>` (repeat for the
  few you actually rely on).
- **<category, e.g. CLI tools>:** `<tool>` — `<why>`.
- **Config pattern:** `<file path>` — `<the setting that matters + its value>`.

Pair durable installs with an idempotent setup script when it's worth automating
(see `engine/setup/NN-*.sh` for the convention); the skill records the *decisions*,
the script applies them.

## When to use

Bringing up a new dev box, auditing what's enabled, or deciding whether a new
tool/extension overlaps something you already run.

## Boundary

Keep it to *your curated choices*, not a generic install tutorial. No machine-specific
secrets or hostnames — parameterize those.
