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
- Workflow first on complex tasks: for any multi-step task — doubly one needing human hands or decisions at more than one point — lay out the ordered workflow before acting (time or logic order, each step's executor marked), offer it for review, then drive. Feeding the human action items piecemeal with no reviewed plan standing is a failure mode even when each individual step is correct; genuine urgency compresses the plan, never skips it.
- A flow that would create an account, profile, or identity as a side effect STOPS and names that fact before proceeding — registration is itself an authority-gate press, never something discovered afterwards.

## Interface investment

- Interface quality sets the price of every human touch — invest in proportion to the decision's weight and recurrence.
- The highest-value interface improvement is usually upstream: fewer decisions reaching the human at all. Automate the mechanical away first, then spend interface richness (context panels, diffs, structured comparisons) on the genuinely judgment-bearing residue.
- Execute-ready by default: when the human must act by hand, deliver the exact steps and content ready to run — the human executes and judges, never reconstructs.

## Harvest the contribution

- Human input is the scarcest signal in the loop — capture it durably. Every correction, preference, and taste call is recorded where the next run reads it, not merely applied once; a system that re-asks what it was already told is burning its rarest resource.
- Human decisions double as calibration data: gate outcomes and quality calls become the labeled set that tunes judges, thresholds, and the automation boundary itself.
