# nervepack-content-example

> A worked example of a **nervepack content overlay**. Fork it, point the engine at it,
> and you've got a working memory + knowledge layer you can fill with your own stuff.

[nervepack](https://github.com/pat-browne/nervepack) ships in two halves. The **engine**
is the reusable machinery (hooks, crons, the toggle system, onboarding, the core
skills). Your **content** is everything personal that the engine reads and writes as
you use it (your own skills, your sources and wiki, the memory it accrues, your
metrics). The two live in separate repos so the engine can be public and shareable
while your content stays yours.

This repo is a filled-in example of that content half. Every layer has one real,
commented file so you can see the shape of the thing instead of guessing at it.

## Use it

1. **Fork or copy** this repo to your own (private) one, say `nervepack-content`.
2. **Point the engine at it.** Write the path into the config the engine reads, or set
   the env var.
   ```bash
   echo "$HOME/Code/nervepack-content" > ~/.config/nervepack/content-dir
   # or, per-shell: export NP_CONTENT_DIR="$HOME/Code/nervepack-content"
   ```
3. **Make it yours.** Replace every `example-*` file with your real content. Rename the
   example skills to `np-kb-<topic>` and `np-env-<thing>`, populate the topic folders
   in `wiki/topics/` with your real sources, and delete the demo memory files under
   `memory/` (the engine regenerates those from your actual sessions anyway).
4. **Relink and go.** Run `engine/setup/30-link-skills.sh` so your skills get delivered
   into every session.

That's really it. From here the engine does the work, and this overlay fills up on its
own as you use it.

## What lives where

The engine resolves these by name directly under your content root, so keep them at the
top level (don't nest them under a `content/` folder).

| Path | What goes here | Who writes it |
|---|---|---|
| `skills/np-kb-*`, `skills/np-env-*` | Your personal knowledge + environment skills (sites, infra, machine setup, brand) | **You** |
| `wiki/topics/<topic>/` | One folder per topic: a `<topic>.md` synthesis page (`kind: topic`) plus co-located source references (`kind: reference`) | You, via the ingest protocol |
| `wiki/concepts/<concept>/` | One folder per concept: a `<concept>.md` synthesis page (`kind: concept`) cross-linking topics, skills, and sources | You / the agent |
| `memory/episodic/<topic>.md` | Auto-captured working memory ("what we did, what we decided") | The `episodic-maintain` cron |
| `memory/lessons/<topic>.md` | Auto-distilled failure + success patterns, tagged `provenance: failure\|success`, with an optional `enforce` block (independent of provenance) that gates the tool call | The `episodic-maintain` cron (don't hand-edit) |
| `dashboard/data/metrics.jsonl` | Per-session performance the evaluator scores and the dashboard renders | The evaluator (don't hand-edit) |
| `docs/superpowers/specs/` | Your design specs and plans (the brainstorm + planning output) | You |
| `log.md` | Append-only audit of everything that lands here | All of the above |

Note that there is **no top-level `sources/` directory** in the canonical layout — sources
live inside their topic folder in `wiki/topics/<topic>/`. And there is **no `wiki/entities/`**
— entities were merged into topic folders; cross-cutting ideas use `wiki/concepts/`.

The two agent-owned layers (`memory/episodic/`, `memory/lessons/`) are filled in here
only so you can see the format. In a real overlay you let the engine write them.

## Sharing an overlay with a team

This same shape works as a **team overlay**. A team keeps one shared repo laid out
exactly like this one (shared skills, lessons, wiki) and each member points at it
*above* their personal overlay:

```bash
echo "$HOME/Code/team-nervepack-content" > ~/.config/nervepack/team-dir
```

The engine reads `team > personal > engine`, highest first. A team skill or lesson
shadows a personal one of the same name, and the topic layers combine per the engine's
`team.merge` setting (`override`, `concatenate`, or `team-only`). Everything you
capture still writes to your *personal* overlay, so a shared baseline never fills up
with one person's session memory. To push something to the team on purpose, say "save
this to the team layer." The team overlay is optional and dormant until you set
`team-dir`.

## A note on what NOT to put here vs. the engine

Personal data lives here, never in the engine. The engine repo has a CI guard that
blocks names, emails, home paths, private hosts, and credentials from landing in it.
Your overlay has no such guard, because it's *meant* to hold your real life. So keep
your overlay private, and keep the engine clean.

For how the engine wires a host and what each feature does, read the engine's
`README.md` and `ARCHITECTURE.md`.
