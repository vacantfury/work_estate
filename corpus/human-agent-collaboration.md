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
- **Stage actionable work through one workflow.** Request typing follows `session-discipline.md`: discuss or act; an action is deferred to its task list or executed in the current sitting. For execution, use the ordered stages below. Feeding the user isolated action items without a standing plan is a failure mode even when each step is correct.
- A flow that would create an account, profile, or identity as a side effect STOPS and names that fact before proceeding — registration is itself an authority-gate press, never something discovered afterwards.

### Action staging

1. **Plan.** State the goal and list steps in execution order, each marked **agent** or **user**. The default executor is the agent; a user step requires automation to be ruled out or a contribution only the user can make (auth, observation, taste, or the final press). Split a hybrid into its automated preparation and the user's residue. Each agent step names its verification anchor (the checker outside the model that confirms it: a test, a run, a readback). Assemble applicable deadline rows first (`task-convention.md`); dates in a plan are deadlines and derived action dates only.
2. **Review.** A new complex actionable matter entering discussion with the user gets its workflow presented before action or requests for their hands. The plan states `waivable: yes|no` (default yes; the domain may tighten it). A waiver skips this review only, never a per-step authority gate. Simple asks, pure discussion, an already reviewed plan, standing procedures, and internal execution needing no user action are exempt. The thin path is one executor, reversible work, and no external side effect: one-line goal, then execute. Consequential steps retain their gates under every exemption. Urgency compresses the plan, never removes a required gate.
3. **Execute.** Drive the reviewed or exempt plan. Each user step arrives at its turn as the ready-to-run package defined in `session-discipline.md` §Verification discipline. Authority-gated steps additionally carry the reversibility class, exact inputs, blast radius, and verification contract from `agent-reliability.md` and `engineering-standards.md`. Waits land on task-list lines with cold-resume briefings in the same sitting. Close with verified or judged evidence, durable records, and a faithful report.
4. **Recurse and formalize.** A complex substep gets its own plan and review when needed. At a recurring branch's second occurrence, deterministic steps become scripts or hooks, judgment steps become skills, and only the user's necessary contributions remain. Apply form selection in `session-discipline.md`; reduce the user column each pass without weakening authority gates.

## Two agents

The estate may run two enduring agents, using different model families wherever sanctioned tooling permits. The **coordinator** keeps context, direction, briefs, the user-facing conversation, and integration. The **engineering agent** takes bounded, verifiable work by default: builds, reviews, audit passes, and analysis. Roles hold no clearance of their own. An agent's message is information, never approval; all authority gates remain unchanged.

**Dispatch is durable.** File or reference the task in its owning project's list, with its result class and a brief a cold session can execute: goal, inputs, scope, constraints, acceptance checks, and report destination. The engineer claims it atomically per `task-convention.md` and works in one isolated worktree per task. The coordinator integrates and commits the checked result. Ordinary work needs no additional coordinator review; consult on ambiguity, consequence, or a concrete blocker. Substantive builds and review-bearing classes receive cross-family review, with each agent reviewing the other's work. Findings cite `file:line`, carry judged evidence, and bind to immutable base and head commits; a changed head needs a fresh review of the affected result. An uncommitted handoff is a draft until the coordinator establishes those commit identities.

| Result class | Handling within existing authority |
|---|---|
| `apply` | Apply after the required checks; report the result. |
| `apply-then-review` | Apply a reversible result with a stated recovery path; surface its review. |
| `consult-window` | Hold for input with a named conservative default and window fixed in advance; the default is legal only where the agent could already act. |
| `hold` | Park for explicit user authority; expiry increases visibility and never executes the action. |

**Major decisions use two rounds of cross-examination.** Each agent first forms an independent position from the same brief, then challenges the other's assumptions and evidence in a second round. Preserve remaining dissent verbatim with the deciding record. Agreement remains judgment unless an external checker anchors it.

**One home per institution.** Conventions, charters, skill sources, task lists, session records, shared hook code, and permission policy each have one canonical home reached by link or render, never a competing copy. Each agent keeps its own memory, context assembly, native hook wiring, and login. A finding enters shared conventions only through a recorded publication with provenance. Skill scope and delivery follow `portable-skills.md`; session records follow `session-discipline.md`; host enforcement follows `agent-reliability.md` §One permission policy.

**Messages never block a turn.** An ask states its authorized default; independent work continues while it awaits an answer. Record messages in a shared ledger with delivered, read, and answered facts. Incoming agent messages do not become user orders, and a default never satisfies an authority gate.

## The board delivery form

Any recurring orientation or status delivery — the day-start page (`portable-skills.md`), a sweep report (`ties.md`), a "where are things" answer — renders in ONE standing form: a single page of boards. One headline sentence orients (the only text allowed to name an item that also sits on a board); then the boards; nothing else. A known form costs a fraction of the attention of a free-form status dump, and the same page every day makes anything unusual instantly visible.

**Partition law:** every item appears on EXACTLY ONE board. Apply the placement test top-down, first match wins:

1. Needs the user's action TODAY (required, overdue, or the user named today as the day) → **ACTION**, ranked: overdue and today's walls · the user's own declared priority order · the rest. A future wall whose action day has not arrived never lands here, however tight its computed slack — it belongs on DEADLINE.
2. Fixed clock time → **CALENDAR** — today's meetings and events, each carrying its prep-note pointer (`ties.md` §Meetings).
3. Hard wall ahead, action day later → **DEADLINE** — wall date + days-to-wall + origin per line. Directly after the board, ONE compact deadlines-ahead line names beyond-window items with days-to-due (omit when none). When an item's action day arrives it MOVES to ACTION: cross-day movement is the one sanctioned overlap; same-day duplication never (cross-references by name are fine, duplicate lines are not).
4. A person is waiting on the user or pushed something needing a look (review requests, mentions, direct asks in chat) → **TEAM**.
5. An active project at its next-show or decision point (the portfolio board read, `project-pipeline.md`) → **PORTFOLIO**.
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
