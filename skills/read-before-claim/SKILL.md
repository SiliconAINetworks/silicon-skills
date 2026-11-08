---
name: read-before-claim
description: Use at the start of every session, after any context compaction or summary, and before stating how something works. The agent reads the real files, handover notes and project rules before it changes, writes or claims anything - never works from memory or from a summary alone.
---

# Read before you claim

After a context compaction an agent remembers the shape of the work but not the details. That is exactly when confident mistakes happen – and the user loses hours correcting them.

## At the start of a session or after compaction

1. Read the project's handover or status notes (e.g. `HANDOVER.md`, `CLAUDE.md`, `AGENTS.md`, `docs/`).
2. Read the project rules and conventions before writing a single line.
3. Check `git log` and `git status` to see what actually happened last.
4. Open the files you are about to touch. The summary says what you meant to do; the files say what is really there.

## Before claiming anything

- **Measure in the code, then speak.** "The worker reads the config on every run" is a claim; point to the line.
- **If docs and code disagree, say so openly.** Do not quietly pick one and smooth it over.
- **Never present something that only exists in the code as the user's plan,** and never present your plan as already built.
- **Don't blame earlier sessions.** "A previous instance broke it" helps nobody. Name the exact spot that is wrong and fix it.

## Tell the user what you read

Start your answer with one short line listing what you checked ("read: handover, rules, git log, `worker.py`"). The user instantly sees whether you are up to date – or whether to stop you.

## Leave a trail

At the end of a work block, update the handover note: what was done, what was decided, what is open, and the exact state (commits, versions, running services). The next session – yours or another agent's – starts there.
