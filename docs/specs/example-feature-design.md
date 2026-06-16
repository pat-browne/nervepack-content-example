# EXAMPLE: <feature name> — design

> **This is the spec TEMPLATE.** Real design specs live here, in your content overlay
> (`$NP_CONTENT_DIR/docs/superpowers/specs/`) — never in the engine repo. This file
> demonstrates *how nervepack writes a spec* so you (or a contributor) can follow the
> convention. Copy it, fill in the `<…>`, and keep your real specs in your overlay.

**Status:** designed `<YYYY-MM-DD>`. `<one line: where it is in its lifecycle>`

**Parent effort.** `<which larger goal this serves, or "standalone">`. Link siblings
with `[[name]]`.

## 1. Goal

- `<the outcome, in 2–4 bullets — what's true when this is done>`
- `<keep it about the WHAT and WHY, not the HOW>`

## 2. Approach

`<2–3 short paragraphs: the chosen design and why. If you weighed alternatives,
name the runner-up and why this won. Reference existing patterns it follows.>`

## 3. Components / changes

| Piece | Responsibility | Notes |
|---|---|---|
| `<file or module>` | `<what it does>` | `<toggle? test? gotcha?>` |

## 4. Invariants / constraints

- `<the rules this must not break — e.g. "fails open", "stays byte-stable",
  "every feature is toggle-gated", "no LLM-attribution in commits">`

## 5. Migration / rollout

`<how it lands safely — incremental steps, what stays green at each, how to roll
back. Omit if not applicable.>`

## Non-goals

- `<what this deliberately does NOT do — scope fences that prevent creep>`
