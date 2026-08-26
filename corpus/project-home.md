# Project home — the per-project scaffold and the record

*The concrete home an accepted project gets under main-work, and the ONE running record it keeps. Split out of `dev-workflow.md` at v6.0.0 so the scaffold has a single owning module: the pipeline (`project-pipeline.md`) decides WHICH projects exist, the dev workflow (`dev-workflow.md`) decides HOW the build runs, this module owns WHERE a project's structure and state live. Team reality first (design principle 10): where the team has a design-doc/status convention, that surface wins and the record holds only what the team surface does not.*

## The scaffold

- An **accept** (or accepted initiative) founds one directory per project under main-work by **copying the shipped template** `main-work/_template/` (installed at unfold from the seed's `skeleton/main-work/_template/` — an estate-local copy, so founding never depends on the seed clone): task surfaces (`TODO.md` headed `# TODO (ordered)`, `NOW.md`, `archive.md`, per `task-convention.md`) plus `record.md`. Copy, fill, register — structure is never re-derived by hand.
- The founding procedure (steps, registry row with edges, board line, premortem) is `portable-skills.md` §project-founding; this module is the shape it instantiates.
- `lessons.md` / `handbook.md` are NOT pre-seeded — they found lazily at the first entry, copied from the hub's `_forms/` (empty shells are clutter).

## The record — `record.md`, one per active project

The standing answer to "why X?" and ready-made readout material. It cites the work record and the portfolio board, never duplicates them. Canonical sections (the template ships them):

- **Design** (dev-workflow Stage A): problem · constraints · success measures (the landing declaration made concrete) · the shape of the whole · which risky assumptions the earliest experiments probe (premortem: the risk register).
- **Decision points and tournaments** (Stages B–C): per consequential decision point, the named candidates (the team incumbent always one) and one line per candidate — what was tried, what killed it or let it survive.
- **Variants** (Stage D): variant · shared seam · eval harness · status.
- **Rung** (Stage E): current environment-ladder position, gate criteria, monitoring notes.
- **Milestones and next-show:** ordered steps (dates only on external walls); the next-show date/venue the board line points at.
- **Landing** (pipeline stage 8): the end declared at accept; the end state when it comes — landed · handed off (receiver, state doc) · killed (short readout).
- **Readouts:** pointers to the stage-event artifacts.

Where the team's design-doc ritual owns the Design section (or more), the record keeps a pointer plus only the residual sections — never a parallel copy of a team surface.

## Lifecycle state lives ON the record

A project's lifecycle state is readable from its record alone: the current rung, the declared landing, the end state. The portfolio board carries the one-line view (`name · stage · sponsor · why-it-matters · next action · next-show`); the record carries the substance. Board and record cite each other; neither duplicates the other.
