# Research workflow — the research lane

*The research arc for an applied-scientist role, ported generically from the owner's personal research workflow (design principle 16). `project-lifecycle.md` governs whether a research effort is taken on and how it lands; `dev-workflow.md` governs how its builds and experiments are staged; this module adds the research-specific arc and the auto-research jobs that run it with minimal owner attention.*

## The arc

A research effort inside a product org walks the same skeleton as academic research, compressed and aimed at a shippable claim:

1. **Question** — one falsifiable question tied to a product/metric outcome; written down before any work.
2. **Grounding — internal first.** Prior art inside the company (docs, past experiments, existing evals, people who tried it — the principle-10 triple source) BEFORE external literature; then the external pass. Grounding output: what is known, what failed before and why, what the question becomes after grounding.
3. **Hypothesis + eval design.** The claim, the eval that would confirm or kill it, and the baseline — settled before building (eval discipline: `role-playbook.md`, `agent-reliability.md`). A result that cannot name its eval is not a result.
4. **Experiment loop.** Runs through the dev-workflow funnel (choice tournaments for method candidates, comparable variants, the environment ladder for anything product-touching); every run one-lined into the project record — question, config, result, verdict, next.
5. **Analysis + honest verdict.** Verified vs judged labels on every claim; negative results are results and are recorded as such.
6. **Readout.** The stage-event artifact (design doc, results readout, demo) riding the team's ceremonies — the research is finished when its claim is communicated and landed per the lifecycle's landing bar, not when the experiments stop.

**Provenance discipline (binding):** every named method states on first mention whether it is established practice/literature (with source) or this effort's own proposal; provenance is checked against the source before being asserted.

## Auto-research jobs (registry entries, `work-engine.md`)

The lane's standing jobs — each writes to its project record or the lane's state, escalates only per its rule:

- **Literature scout** — periodic sweep of the field's new work relevant to active questions (external sources the tooling sanctions; internal research feeds first where they exist); output: a short delta note per active project, not a reading list.
- **Internal prior-art scout** — standing watch on internal docs/experiment records adjacent to active questions; new relevant prior art is a grounding update, sometimes a kill signal — escalate a kill signal.
- **Eval-landscape watch** — what benchmarks/evals/judge practices the field and the org are moving to for the active problem class; feeds stage 3.
- **Experiment monitor** — running jobs triaged (failed runs, anomalous metrics, done-ness); result lines drafted into the project record; escalate anomalies that block the loop.
- **Analysis and writing assists** — drafting the analysis pass and readout artifacts from the project record for the owner's taste-judge pass.

## Fit with the rest

A research effort IS a project: it lives on the portfolio board, competes in prioritization, and lands explicitly. What this module adds is the arc's research-specific stages (question/grounding/hypothesis rigor) and the standing jobs; everything else — selection, negotiation, sync cadence, landing — is the lifecycle's, unchanged.
