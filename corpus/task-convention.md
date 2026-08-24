# Task convention (portable)

The ordered-TODO task system. Plain markdown, human- and machine-readable, tooling-agnostic.

## The file

- One `TODO.md` per workspace, at the root. Header: `# TODO (ordered)`.
- **Position = priority.** The list's order IS the ranking; no separate score fields, no priority labels.
- It is personal working state, not product: keep it out of version control in shared repos (gitignore it) unless the team explicitly runs a shared list.

## Core rules

- **One home per item.** A task lives in exactly one list, chosen by where the work executes. Move it when the locus changes — never copy; a task written in two places will desynchronize.
- **Adding never reorders.** Append new items to the tail (or a capture inbox). Ranking happens deliberately, in batch passes — never ad hoc for one arriving item.
- **Grasp the big, release the small.** Ranking distinguishes important from minor and acts on it twice over: selection (drop or shrink the minor rather than do everything) and sequence (the big never waits behind the small).
- **Every session maintains the TODO of the workspace it works in.** Completions and material advances are recorded in the same session they happen.
- **Finished and dropped items move to an archive file** (e.g. `archive.md`), one line each: `<close-date> · [done|dropped] · task text · [added: YYYY-MM-DD]`. Records are kept, never deleted. Never guess a missing date — write `[added: ?]`.
- **Rules that never complete are not tasks.** Recurring invariants belong in the conventions/instructions layer, not the TODO.
- **Task files and records are written in plain English,** whatever language the input arrived in (translate at intake, no glosses); human names may keep their native script.
- **Items are cited to the user by position, never by id:** "item 2" plus a few words of the item's text. Under the store-backed form (§below), the machine ids on view lines are addresses for tooling only and still never appear in text written for the user.

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

## The store-backed form (the standard form where a store engine exists)

Once the estate's store engine exists (`store.md`, resolved at unfold A7), each task list runs **store-first**. The markdown form above remains the bootstrap and the degraded fallback; its line conventions are deliberately flip-ready. The spec below is implementation-grade: the estate's sanctioned agent builds the tool against the A7 engine at founding, and every rule above (one home, adding never reorders, archive lines, states, annotations, cite-by-position) carries over unchanged.

- **The store is the truth; `TODO.md` is a generated view.** The view opens with a banner line naming the store and the write path, so no session mistakes it for a hand surface. The view regenerates after every write.
- **Row shape:** stable integer id (assigned once, never reused) · title · state (active / dormant-after / dormant-when / waiting / someday) · rank among active rows (position = priority, preserved exactly) · the coarse annotations as line tags · added-on stamp · owning project.
- **Append-only status ledger:** every state change, note, and close appends a dated ledger row; nothing is overwritten. Close records `done` or `dropped` and emits the one-line archive entry in the convention above.
- **Writes go through verbs, never file edits:** `add · close · note · edit · state · rank · wake · show · list · regen · ingest · verify`. Stamps are automatic. Adding never reorders (new rows join the tail); `rank` is the deliberate batch reorder.
- **The view:** a numbered active section in rank order, then sections for dormant / waiting / someday; every line ends with `[id: tN]` — a machine address for tooling, never cited to the user. Free-write tail sections (a capture inbox, an auto-maintained block) survive regeneration behind a declared marker line.
- **Hand edits are input, never violations:** a content hash detects an edited view, and `ingest` absorbs it — a reordered active section is the user's ranking, an edited line updates its row, an id-less line becomes a new row, and a DELETED line is reported for confirmation, never silently closed. Mutating verbs refuse over an un-ingested view, so nothing is clobbered.
- **Wake is a standing job:** dormant `[after:]` rows wake automatically on their date, through the ledger; the engine's cycle runs it (session-opening sweep on a degraded install).
- **Flip once, keep the backup:** an existing markdown list flips by parse-and-load — content preserved verbatim, ids assigned at flip, the pre-flip file kept beside the view. From then on there is ONE write surface; any older sync path refuses.
- **Verify is cheap and standing:** `verify` checks the view against the store; the estate self-audit reads it.

## Cold-resume briefings

A parked in-flight task carries its resume package on the task line itself: what is done, the exact next command ready to run, and how to verify. A future session (or a future you) must be able to resume without reconstructing context.

## Deadline buffer

Any action against an external wall — submission, filing, registration, renewal, payment — is scheduled **at least two days before the wall**, and every plan/TODO line states the buffered date, not the wall date.
