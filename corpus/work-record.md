# Work record — the running log of everything done

*A time-ordered record of what was actually done, day by day — ALL of it, across projects and around them (settled 2026-08-14). Two layers: a **private record**, full-grain, on the work machine — the single truth; and a **public view**, a curated rendering for the manager and team, derived from it and never separately maintained. The record is the memory the role runs on: status answers, the weekly debrief, and review-time impact evidence are all reads of it, never reconstructions.*

## What it is — and what it is not

- It records **activity**: what was done in a day — delivered and progressed work, meetings and reviews, help given, operational interruptions, things learned.
- It is **not the project tracker.** The portfolio board (`project-lifecycle.md`, `local/state/projects.md`) holds per-project state, and each project keeps its own working notes. The work record CITES projects by name and never duplicates their state — one line "advanced X: <what moved>", the substance living in the project's own home.
- Sibling stores keep their own lanes: health events → the health tracker (`health-guard.md`); company signals → the company store (`company-watch.md`). The record may point; it never re-homes.

## The private record — `local/state/worklog.md`

Unfold-seeded, work-local, append-only by day:

```
# Work record — private, full grain

## YYYY-MM-DD
- site: <on-site | remote | out (leave/holiday)>
- did: <delivered or progressed item, one line> (project: <name>)
- meet: <meeting/review/1:1 — what it was + outcome one-liner>
- helped: <who was unblocked / reviewed / advised>
- ops: <interruptions, maintenance, on-call, overhead>
- learned: <new tool, system, or fact worth keeping>
- note: <candid free grain — friction, time sinks, judgment calls>
```

**Capture discipline:** cheap and continuous, never a reconstruction ceremony. A session appends what IT did as it closes (session-end capture — the same reflex as capture-at-settle, `session-discipline.md`); the user adds the lines only they know (meetings, hallway conversations, their own manual work) — a one-minute end-of-day pass suffices. A day with no entry is a visible gap, not a silent one.

**Record posture** (the standing ruling, settled 2026-08-12/13, applied here): the private record lives ON the work machine, candid and complete, kept for the user's benefit — what a task actually cost, what dragged, honest working notes. The user's own work activity is knowledge legitimately theirs; completeness is never traded for appearance. Conservatism about the user's own content on the work device applies only on real risk or real company conflict, never by default.

**Presence tracking** (design principle 20c): the daily `site:` line is the ground truth of on-site attendance. Design principle 9 sets the presence POSTURE (calibrated to the real team norm); this field records the DATA, so presence is managed from evidence, never impression. A periodic tally (on-site days over working days, monthly by default) is read against the written policy floor and the real team norm intake §10 discovered; drift below either surfaces in the weekly debrief, never silently — and never as pressure beyond what the norm itself implies.

## The public view — a rendering, never a second truth

The manager-and-team-visible version is **derived from the private record — one direction, private → filtered → public.** Two parallel records are never maintained; the public view is re-rendered from the private truth at its cadence (the dual-truth ban).

- **What renders public:** delivered and progressed work, collaboration and reviews, results with their evidence — written in the team's idiom for its actual readers (the manager scanning status, teammates coordinating).
- **What stays private:** the candid grain — friction, time accounting, half-formed judgments, health-adjacent notes, company-watch observations. Curation is audience-writing, not concealment: everything public is true; not everything true is the reader's business.
- **Default shape** (used only until the team's own convention is discovered): a weekly section — done · in progress · next · asks/blockers, a few lines each.

## Where the public view lives — resolved at intake, never assumed

The team very likely already has a status-record convention — weekly snippets, standup posts, sprint readout notes, a wiki/status page, a running 1:1 doc the manager keeps. Discovery (intake §15, `knowledge/week1-intake.md`) follows the standing grounding rule: **the team's docs and artifacts first, then ask** — the manager ("where would you want to see a running record of my work, and at what cadence?") and a teammate ("where does status actually get posted and read here?"). The discovered convention WINS over this module's default shape and home (design principle 10). Until resolved, the rendering stages at `local/state/worklog-public.md`, ready to move into whatever home the answer names.

## Cadence

- **Private capture: daily** — sessions continuously, the user's one-minute pass at day end.
- **Public render: the team's rhythm** — ride an existing ceremony where one exists (standup, sprint readout, a snippets cadence); weekly by default otherwise. A render is a read-and-distill of the period's private entries — minutes, not hours.

## Consumers — why the record pays

- **Manager alignment:** this is the concrete mechanism behind the playbook's "running shared record of delivered work" — the review conversation holds no surprises because the public view already told the story all period (`role-playbook.md`, working in the org).
- **The weekly debrief (format home: HERE):** at week's end the record distills into a seven-line summary appended to the worklog — `## Debrief (week of YYYY-MM-DD)`: role (how the work is going) · growth (skills/scope/evidence) · people (relationship developments, meaning grain) · load (light|normal|heavy|crunch, plus one line why if not normal) · health (floors held | breaches n (which), from the health-guard tracker, plus a strain one-liner) · presence (on-site n of m working days, vs the policy floor and team norm) · events (review cycles, org changes, milestones). Distilled from the week's record — a read, not a reconstruction; the record grain rule (`boundary-protocol.md`) governs it like every record. The user reads it at week's end.
- **Review-time evidence:** impact narratives at review time assemble from dated record lines, not from memory.
- **Cold-session memory:** any session answering "what happened last week / what did I do on X" reads the record.

## Fold-away note (for the unfold's A5 pass)

Core-adopt at every policy outcome — one local file plus minutes a day. Only the public view's home and cadence vary: they follow the team convention intake §15 discovers.
