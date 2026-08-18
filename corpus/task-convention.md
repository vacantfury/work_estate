# Task convention (portable)

The ordered-TODO task system. Plain markdown, human- and machine-readable, tooling-agnostic.

## The file

- One `TODO.md` per workspace, at the root. Header: `# TODO (ordered)`.
- **Position = priority.** The list's order IS the ranking; no separate score fields, no priority labels.
- It is personal working state, not product: keep it out of version control in shared repos (gitignore it) unless the team explicitly runs a shared list.

## Core rules

- **One home per item.** A task lives in exactly one list, chosen by where the work executes. Move it when the locus changes — never copy; a task written in two places will desynchronize.
- **Adding never reorders.** Append new items to the tail (or a capture inbox). Ranking happens deliberately, in batch passes — never ad hoc for one arriving item.
- **Every session maintains the TODO of the workspace it works in.** Completions and material advances are recorded in the same session they happen.
- **Finished and dropped items move to an archive file** (e.g. `archive.md`), one line each: `<close-date> · [done|dropped] · task text · [added: YYYY-MM-DD]`. Records are kept, never deleted. Never guess a missing date — write `[added: ?]`.
- **Rules that never complete are not tasks.** Recurring invariants belong in the conventions/instructions layer, not the TODO.

## States (before scores)

Only ACTIVE items compete for order; everything else waits below or is annotated.

- **active** — competing for attention now
- **dormant `[after: YYYY-MM-DD]`** — auto-wakes on the date
- **dormant `[when: <event>]`** — woken by judgment when the event happens
- **`[waiting: <who/what>]`** — blocked on someone or something else
- **someday** — kept without commitment

## Annotations (all optional, coarse)

- `[due: YYYY-MM-DD hard|soft]` — real external deadlines only, never self-imposed pressure
- `[value: A|B|C]` — coarse value tier
- `[~30m|~1h|~2h|~days|~weeks]` — effort
- `[brain: low|med|high]` — cognitive drain (thinking load, pressure), NOT duration
- `[added: YYYY-MM-DD]` — stamped by whoever first writes the task
- `[unlocks: <what>]` · `[sooner-better]` · `[idea]` — coarse routing hints
- Watch tags: `[cadence: Nd|Nw]` or `[checks: d1, d2, …]` + `[checked: YYYY-MM-DD]` — the task is HELD between checks; exhausted checks = due: extend or close
- `[escalate: YYYY-MM-DD]` — forces top urgency if the date arrives unresolved

Urgency is computed from these at read time, never stored as a field.

## Cold-resume briefings

A parked in-flight task carries its resume package on the task line itself: what is done, the exact next command ready to run, and how to verify. A future session (or a future you) must be able to resume without reconstructing context.

## Deadline buffer

Any action against an external wall — submission, filing, registration, renewal, payment — is scheduled **at least two days before the wall**, and every plan/TODO line states the buffered date, not the wall date.
