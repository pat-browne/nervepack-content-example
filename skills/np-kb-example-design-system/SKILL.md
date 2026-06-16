---
name: np-kb-example-design-system
description: TEMPLATE — copy into your content overlay and rename to np-kb-<yourname>. Captures your project's visual identity (colors, type, spacing, components) so the agent defaults to your system instead of inventing values. Use when making any UI/design decision.
---

# EXAMPLE: a design-system knowledge skill

> **This is a template, not a live skill.** This whole repo is an *example* content
> overlay. To use it for real: copy this dir into your own (private) content overlay
> (`$NP_CONTENT_DIR/skills/`), rename to `np-kb-<something>`, replace the placeholders
> with your real values, and re-run `engine/setup/30-link-skills.sh`. Keep your real
> one private — it captures your brand.

This shows the *shape* of a `np-kb-` design/branding skill. Replace every `<…>`.

## Tokens (the canonical values the agent should default to)

- **Colors:** background `<#hex>`, surface `<#hex>`, text `<#hex>`, accent `<#hex>`,
  border `<#hex>`. (List the few you actually reuse — not a full palette dump.)
- **Type:** body `<font stack>`, headings `<font stack>`, mono `<font stack>`; base
  size `<px>`, scale `<ratio>`.
- **Spacing / radii / shadow:** base unit `<px>`; radii `<sm/md/lg>`; shadow `<value>`.

## Component patterns

Describe the 2–4 components you reuse most (button, card, input…) as decisions, not
code — e.g. "Buttons: `<radius>` radius, `<padding>`, accent fill on primary, never
pure-black text (use the text token)."

## Why this is a skill, not a config file

The agent reads this *before* designing, so it picks your values instead of generic
defaults. Keep it lean (the decision belongs here; long rationale → `references/`).
