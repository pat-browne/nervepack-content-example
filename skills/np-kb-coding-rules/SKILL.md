---
name: np-kb-coding-rules
description: A generic starter ruleset applied to every project — think before coding, simplicity first, surgical changes, goal-driven execution, no destructive data changes, native-tools-by-default, lock down anything you expose, skill/checklist-first on review tasks, audit consumers after moving a path. Use when writing, editing, or reviewing any code unless the project's own instructions override. Starting point — adapt or extend it for your own conventions.
---

# Coding rules

A generic, reusable ruleset for any coding agent. Project-specific instructions
(a repo's own `CLAUDE.md`/`AGENTS.md`/`.cursorrules`) override where they conflict.
This is a **starter set** — copy it into your own content overlay and extend it
with your own conventions and links as they accumulate.

## 1. Think before coding

State assumptions. If multiple interpretations exist, surface them — don't
pick silently. If something is unclear, stop and ask.

## 2. Simplicity first

Minimum code that solves the problem. No speculative features, no abstractions
for single-use code, no error handling for impossible scenarios. This applies to
*architecture*, not just code: prefer a tool's built-in capability over bolting
on external services, and when scoping a solution offer the smaller option first.
When in doubt, propose less — an unnecessary abstraction or dependency is a cost
paid by everyone who reads the code later.

## 3. Surgical changes

Touch only what the request requires. Don't refactor adjacent code, don't
reformat, don't delete pre-existing dead code unless asked.

## 4. Goal-driven execution

Convert tasks into verifiable goals. "Fix the bug" → "write a failing test,
then make it pass". For multi-step work, state the plan and the check for
each step.

## 5. Never wipe user data on a schema change

When you change the shape of anything persisted (storage, settings, DB rows,
config files, saved documents), **migrate existing data losslessly** — users who
already installed/used the prior version must keep their content. Concretely:

- Read-migrate old shapes into the new one (when widening a scalar into a
  collection, keep the old value as the first element). Migrate on read so
  nothing is lost even before the next write.
- **Add an explicit upgrade test** that seeds the *previous version's* exact shape
  and asserts the content survives — including across a subsequent save (the
  write that drops the legacy key must not drop the data).
- Treat "don't destroy what users already have" as a release gate for any
  feature that touches a persisted schema. New features never justify data loss.

## 6. Native code tools are the default

Default to native read/grep/glob/edit tools for code navigation and editing —
they have no startup cost and no extra moving parts. Reach for a symbolic or
LSP-aware tool (a language server's go-to-definition/find-references, a
project-indexing MCP server, structural search-and-replace like `ast-grep`)
only when a codebase is large enough that plain text search genuinely misses
things or an accurate rename needs symbol-level understanding. On a small
repo, the always-on overhead of a heavier tool rarely pays for itself —
measure before defaulting one on for every project.

## 7. Lock down any service you expose — "localhost-only" is not a security boundary

When you stand up an HTTP server (or any listener) with **state-changing routes**,
defend it even on `127.0.0.1`. A loopback bind stops remote TCP, not a web page the
user visits: a cross-origin `fetch`/form can POST to `http://127.0.0.1:<port>/…`, and
**DNS-rebinding** reaches a naive bind via an attacker hostname. Minimum bar:

- A **CSRF guard** on every mutating route — require a loopback `Host`, a loopback
  `Origin` when one is sent, **and** a custom header the legitimate page sets (a
  cross-origin form POST can't add a custom header without triggering a CORS
  preflight, which you refuse). Reject anything missing the header with `403`.
- **Path-sanitize** anything mapped to the filesystem — resolve the requested path
  and verify it falls under the served root before touching disk; block `../`
  traversal explicitly.
- A **fixed route allowlist** rather than a catch-all handler.
- Argv-list subprocess arguments (never build a shell string from request input).
- Bind loopback, and default the whole listener to **off** unless the user
  explicitly enables it.
- A test that a header-less mutating request gets `403`.

## 8. Invoke the governing skill or checklist before reading files on a review task

Before opening any file or running any grep on a security, review, audit, or
compliance-check task, look for and invoke the tool/skill/checklist that
governs that task type (a security-review skill, a code-review skill, a
linter or audit checklist) rather than deriving the checklist from scratch
each time. A written checklist holds the scope rules and the failure patterns
already learned from past reviews; opening files first tends to produce
inconsistent coverage and re-derives guidance that's already written down.
Let the checklist drive which files to open and in what order.

## 9. After moving a path, audit every consumer — not just the obvious callers

Relocating anything code reads by path (a config/content directory, a file, or
a directory that becomes a symlink) rarely breaks at the move itself — it
breaks at a reader left pointing at the old location. Grep for *every*
consumer across the whole codebase, not just the language or module you
changed, and fix each one with a regression test. Watch in particular for:

- **A consumer in a different language than the code you changed** — a
  hardcoded default reimplemented instead of resolved through a shared
  lookup, so it keeps pointing at the old location.
- **A path/security guard that canonicalizes the path** (e.g. resolves
  symlinks before checking it's under an allowed root) — it can start
  *rejecting* something the move turned into a legitimate symlink.
- **A generator that merges private and public views** and writes into a
  surface that's supposed to be public-only — a move that changes what gets
  merged can leak something into a guarded public artifact.

Docs and other skills/checklists are consumers too — a written reference to a
path can go stale exactly like code can.

## When to extend this

This is a deliberately generic starting point. As you use it, you'll accumulate
your own project- or team-specific rules (commit conventions, deployment gates,
domain-specific migration patterns) — add them here or split them into their own
skill and cross-link back to this one.
