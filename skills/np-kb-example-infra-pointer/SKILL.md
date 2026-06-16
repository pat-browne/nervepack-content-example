---
name: np-kb-example-infra-pointer
description: TEMPLATE — copy into your content overlay and rename. Points the agent at a piece of infrastructure you own (a site, a server, a self-hosted service) — where the repo is, the stack at a glance, how to reach it, which creds/profile to use. Use when working on that system so the agent doesn't rediscover it each time.
---

# EXAMPLE: an infrastructure-pointer knowledge skill

> **Template, not a live skill** (see the EXAMPLE design-system skill for how to adopt
> it). Copy into `$NP_CONTENT_DIR/skills/`, rename to `np-kb-<system>`, fill in your
> real details, keep it **private** (it names your infra). Replace every `<…>`.

A pointer skill is a few durable facts about a system you own, so the agent starts
from "I know where this lives and how it's built" instead of asking.

## <system name> at a glance

- **Repo:** `<github org/repo or path>` (`<private|public>`)
- **Stack:** `<framework / hosting / key services>`
- **Reach it:** `<URL>` / `<host:port>` / `<how to SSH or connect>`
- **Creds:** `<which profile / secret name>` — pulled via your secrets workflow, never
  inlined here. **No raw secrets, tokens, IPs-you-consider-sensitive, or passwords in
  a skill.**
- **Authoritative docs:** `<where the real docs live>`

## When to use

"Working on `<system>`, deploying it, or wiring something to it" → read this first.

## Boundary

This is a *pointer* (durable orientation), not a runbook. Step-by-step procedures and
anything version-sensitive belong in the repo's own docs or a `references/` file.
