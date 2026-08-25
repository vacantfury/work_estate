# Human–agent collaboration design

Conventions for designing the human's place in agentic workflows — both as personal working discipline (where to put oneself in one's own agent loops) and as product-design vocabulary for human-facing agent features. Provisional like every module: where the team has an established practice, the team practice wins.

The one-sentence thesis: **human participation improves results exactly where the human holds comparative advantage; everywhere else it adds latency and noise, and quietly makes human memory and discipline a load-bearing dependency.** The design question is never "how much human?" but "which human contributions, at which typed points, at what interface cost?"

## Typed human roles

- Type every human touchpoint by the contribution it actually makes: **spec-setter** (owns intent and success criteria), **taste judge** (quality calls no checker captures), **ground-truth source** (observes what the system cannot), **authority gate** (approval on irreversible or consequential steps). A touchpoint that fits none of these is a candidate for automation.
- The authority gate is for authority, never epistemic rescue (see `agent-reliability.md`): every escalation carries the system's own recommendation, because the epistemic work belongs to the system.
- The boundary is empirical, not ideological: default pressure toward less human involvement, but a measured failure deficit adds a gate or check back. Neither "full auto" nor "human in every loop" is a design position — the outcome record is.

## Standardized choice surfaces

- Decisions reach the human in ONE known format: the concrete options, one recommendation with its reason, the do-nothing consequence, the named default. A decision arriving in a known format costs a fraction of the attention of a free-form "what should we do?"
- At every choice point, name the exact intended option and pre-empt the plausible wrong one — never leave a branch to the human's guess.
- Fewer, richer decision points beat many shallow confirmations. Approval fatigue is a real failure mode: a gate the human has stopped reading is a heuristic control pretending to be structural.
- Workflow first on complex actionable matters: when a new multi-step actionable matter enters discussion with the human (they raise it, or they engage one the system surfaced), lay out the ordered workflow before acting (time or logic order, each step's executor marked), offer it for review, then drive. Not fired by simple asks, pure discussion, work already under a reviewed plan, standing procedures, or purely system-internal execution; the narrow scope is deliberate — the broad "any complex task" form would add review touchpoints to work the human never needed to see. Feeding the human action items piecemeal with no standing plan is a failure mode even when each individual step is correct; genuine urgency compresses the plan, never skips it.
- A flow that would create an account, profile, or identity as a side effect STOPS and names that fact before proceeding — registration is itself an authority-gate press, never something discovered afterwards.

## The board delivery form

Any recurring orientation or status delivery — the day-start page (`portable-skills.md`), a sweep report (`ties.md`), a "where are things" answer — renders in ONE standing form: a single page of boards. One headline sentence orients (the only text allowed to name an item that also sits on a board); then the boards; nothing else. A known form costs a fraction of the attention of a free-form status dump, and the same page every day makes anything unusual instantly visible.

**Partition law:** every item appears on EXACTLY ONE board. Apply the placement test top-down, first match wins:

1. Needs the user's action TODAY (required, overdue, or the user named today as the day) → **ACTION**, ranked: overdue and today's walls · the user's own declared priority order · the rest. A future wall whose action day has not arrived never lands here, however tight its computed slack — it belongs on DEADLINE.
2. Fixed clock time → **CALENDAR** — today's meetings and events, each carrying its prep-note pointer (`ties.md` §Meetings).
3. Hard wall ahead, action day later → **DEADLINE** — wall date + days-to-wall + origin per line. Directly after the board, ONE compact deadlines-ahead line names beyond-window items with days-to-due (omit when none). When an item's action day arrives it MOVES to ACTION: cross-day movement is the one sanctioned overlap; same-day duplication never (cross-references by name are fine, duplicate lines are not).
4. A person is waiting on the user or pushed something needing a look (review requests, mentions, direct asks in chat) → **TEAM**.
5. An active project at its next-show or decision point (the portfolio board read, `project-lifecycle.md`) → **PORTFOLIO**.
6. Otherwise-ranked work → **MAIN** — the TODO head in rank order.
7. Awareness only → **KNOWLEDGE** — terse FYI lines.

**Line rules:** uniform anatomy `[source] · what · when-marker · pointer`. One visible line per item — never a prose fold or a ·-joined compression of several items into one line. A re-listed unclosed item carries its age ("since MM-DD"). Items sharing one wall may share one grouped line. **Normal-length-or-absent:** every line is self-explanatory at a read — full phrases, names spelled out, no cryptic fragments; an item not worth a readable line drops to its home (or the counts tail), never onto a board compressed. Compression reduces the number of lines, never a line's readability.

**Silence rules:** empty boards say NOTHING. Deliberately NO waiting board — waiting state lives on task and thread rows and surfaces only as due nudges. An item the user has assigned to another venue leaves the boards; its owning home tracks it. Close with ONE counts/degradation tail line (skipped-bulk counts, stale-source warnings); a real error gets its one line, never silence.

**Numbering:** the ACTION board's numbering IS the delivery's reference numbering — the user cites items by position; no second manifest or summary table is layered on top of the boards.

The board SET adapts per install (an estate with no portfolio pipeline drops PORTFOLIO; a domain that earns standing attention may add its own board). The partition law, line anatomy, and silence rules are the form.

## Interface investment

- Interface quality sets the price of every human touch — invest in proportion to the decision's weight and recurrence.
- The highest-value interface improvement is usually upstream: fewer decisions reaching the human at all. Automate the mechanical away first, then spend interface richness (context panels, diffs, structured comparisons) on the genuinely judgment-bearing residue.
- Execute-ready by default: when the human must act by hand, deliver the exact steps and content ready to run — the human executes and judges, never reconstructs.

## Harvest the contribution

- Human input is the scarcest signal in the loop — capture it durably. Every correction, preference, and taste call is recorded where the next run reads it, not merely applied once; a system that re-asks what it was already told is burning its rarest resource.
- Human decisions double as calibration data: gate outcomes and quality calls become the labeled set that tunes judges, thresholds, and the automation boundary itself.
