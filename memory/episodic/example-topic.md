---
name: example-topic
kind: episodic
last_updated: 2026-06-16
wiki: ["np-kb-example-design-system"]
projects: ["acme-widget"]
---

# Example Topic

> **Template — and normally you would NOT hand-write this.** The episodic layer is
> **agent-owned**: the daily `episodic-maintain` cron drains your session inbox into
> themed `episodic/<topic>.md` files automatically. This file is here only to show the
> *shape* of what that agent produces. It's the lowest-authority layer — working
> narrative, may be stale, prunable. Durable rules belong in a skill, not here.

## [2026-06-16] acme-widget — wired the design system into the new dashboard

Built the acme-widget dashboard shell and pulled the color/type tokens from
`np-kb-example-design-system` instead of inventing values. Decided to defer the dark
theme until the token set is finalized. Left off: the empty-state illustration still
needs a real asset; tracked as a follow-up.
