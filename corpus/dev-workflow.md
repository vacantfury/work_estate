# Development workflow — the staged funnel

*How an accepted project is executed: **decisions settled by cheap evidence, never by upfront commitment or debate.** At every level — tool and structure choices, whole-product variants — multiple candidates enter, small experiments eliminate the clearly bad, and the survivors advance to the next, more expensive stage; the funnel runs through an environment ladder to a declared completion, and produces its own reporting material at every transition. Team reality first (design principle 10): wherever the team has a real process for a stage — a design-review ritual, staging environments, an experimentation platform, release trains — that process IS the stage; this module fills gaps and governs personal discipline. The concrete rungs and rituals are discovered at intake (`knowledge/week1-intake.md` §16), never assumed.*

## Proportionality — how much funnel a build earns

- Candidate count, variant count, and rung formality scale with the **cost of being wrong plus the cost of changing later**. An irreversible or expensive-to-migrate choice earns the widest tournament; a cheap reversible choice is simply made — mature default, revisited only if it hurts. A bugfix or small increment collapses the stages to edit → local test → the team's pipeline.
- A pre-experiment that costs more than switching later would is worse than none. Ceremony is never the point; eliminating real risk cheaply is.

## Stage A — whole-product design

- One design pass before building: the problem, constraints, success measures (the pipeline's landing declaration made concrete), and the shape of the whole. It goes through the team's design-doc/review ritual where one exists; otherwise it is the record's Design section (`project-home.md`).
- The accept-time premortem (`risk-register.md`) aims the funnel: the design names which risks and assumptions the earliest experiments should probe, so the riskiest assumption is killed or confirmed at the cheapest possible stage.

## Stage B — substructure design and decision points

- Decompose the product into components with clean seams; per component, name the **decision points** — the tool, library, model, and structure choices that would be expensive to revisit later.
- Every consequential decision point gets **named candidates** (typically 2–4), generated honestly — the team's incumbent or default enters every tournament as a candidate, and is often the strongest one.

## Stage C — choice tournaments (pre-experiments)

- No consequential choice is settled by debate, fashion, or reading documentation alone. Each candidate gets a **small, time-boxed pre-experiment** against the few criteria that actually matter for that component (drawn from the design's success measures: quality, latency, cost, operability, team fit).
- The purpose is **elimination, not perfection**: exclude the clearly-too-bad cheaply; the survivors — one or a few — advance. A tournament that cannot distinguish its candidates at this cost is itself a finding: the choice matters little, take the incumbent or the mature default and move on.
- Every tournament closes with one line per candidate in the project record: what was tried, what killed it or let it survive. This record is the standing answer to "why X?" and ready-made readout material.

## Stage D — variant build

- Where surviving choices genuinely differ, the whole product is built as **a few variants** — typically two or three, sharing the common substrate behind the same seam — rather than betting everything on one. Variants stay comparable: same interface, same eval harness, same measurements.
- One variant is fine when the tournaments converged. The opposite failure is carrying variants nothing ahead can evaluate: variant count is set by what the ladder can actually test.

## Stage E — the environment ladder

Each promotion is a gate with declared criteria; each rung both tests and **monitors**:

1. **Local:** the full test suite plus the project's own eval harness. Nothing leaves the machine failing here.
2. **Test environment:** deploy the surviving variants to the team's shared test/staging/dogfood rung (whatever intake found); run the declared test plan; watch the environment's real telemetry, not just exit codes. A variant that fails or clearly loses exits here — recorded, not mourned.
3. **Production:** the surviving **one or two** variants ship through the team's real release ritual (canary → flighted experiment → ramp, where those exist — the playbook's per-release loop is the LLM-product instance). Monitoring continues after ship: production behavior feeds the error-analysis loop, a regression is a rung failure like any other, and the previous configuration stays restorable until the ramp completes.
4. **Complete:** declared, never assumed — the lifecycle's stage-8 landing bar (shipped + measured + presented + credited); the project record closes with the final readout.

## Reporting rides the funnel

- **Progress reports and presentations are stage events, not afterthoughts.** Every transition yields a naturally showable artifact — the design readout, tournament results ("four candidates, two killed, here's why"), the variant comparison, test-environment results, the launch readout — delivered on the lifecycle's sync cadence (`project-pipeline.md` stage 7) through the team's own ceremonies.
- The funnel makes status honest by construction: the report IS the record, filtered for its audience (`work-record.md`'s render rule), never a parallel narrative.

## The project record

- Each active project keeps ONE running record; its home, canonical sections, and shipped template are owned by `project-home.md` — the funnel's stages write the record's Design / Decision-points / Variants / Rung sections as they run. The team's design-doc/status convention wins where one exists.
