---
name: example-topic
kind: lesson
provenance: failure
status: candidate
seen: 2
last_updated: 2026-06-16
topic_triggers: [example, placeholder, template, demo]
enforce:
  tool_match: ""
  gate: warn
wiki: []
---
**Symptom:** `<the recurring failure or correction the agent keeps hitting — described
so a future session recognizes it.>`
**Why:** `<the root cause, in one line.>`
**Do:** `<the intervention that works — concrete and actionable.>`
**Avoid:** `<the tempting-but-wrong move that caused the failure.>`

> **Template — agent-owned.** Playbooks are **auto-distilled** by the `episodic-maintain`
> cron from `struggles[]` your sessions emit, then **enforced at runtime**: a `warn`
> gate injects this guidance at the tool call; an `ask` gate pauses for confirmation.
> `tool_match` empty + `topic_triggers` set = advisory injection via `UserPromptSubmit`
> (used when the guidance targets a non-Bash tool like Read/Edit). Precedence:
> `skills > sources > wiki > playbooks > episodic`. A proven playbook graduates to a
> `skills/np-kb-*` rule via human review — don't hand-edit this layer.
---
name: example-topic
kind: lesson
provenance: success
status: candidate
seen: 2
last_updated: 2026-06-16
topic_triggers: [example, placeholder, template, demo]
wiki: []
---
**Title:** `<a reusable success pattern, named so future-you recognizes it.>`
**When:** `<the situation where this approach applies.>`
**Do:** `<the approach that worked — concrete enough to repeat. Strategies are the
success mirror of playbooks: where a playbook says "avoid this failure," a strategy
says "when X, the approach that worked is Z.">`

> **Template — agent-owned, advisory.** Strategies are auto-distilled by
> `episodic-maintain` from the `strategies[]` your sessions emit, and surfaced via
> `strategy-recall` on a matching prompt. Unlike playbooks they are **not enforced** —
> they're injected as advice. Same second-class status; don't hand-edit.
