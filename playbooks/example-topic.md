---
name: example-topic
kind: playbook
status: candidate
seen: 2
last_updated: 2026-06-16
enforce:
  tool_match: ""
  gate: warn
  topic_triggers: [example, placeholder, template, demo]
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
