# Research workflow — the research lane

*The research arc for an applied-scientist role, ported generically from the maintainer's established research workflow (design principle 16). `project-pipeline.md` governs whether a research effort is taken on and how it lands; `dev-workflow.md` governs how its builds and experiments are staged; this module adds the research-specific arc; the standing jobs and candidate funnel that run the lane with minimal user attention are `auto_research.md`'s.*

## The arc

A research effort inside a product org walks the same skeleton as academic research, compressed and aimed at a shippable claim:

1. **Question** — one falsifiable question tied to a product/metric outcome; written down before any work.
2. **Grounding — internal first.** Prior art inside the company (docs, past experiments, existing evals, people who tried it — the principle-10 triple source) BEFORE external literature; then the external pass. Grounding output: what is known, what failed before and why, what the question becomes after grounding.
3. **Hypothesis + eval design.** The claim, the eval that would confirm or kill it, and the baseline — settled before building (eval discipline: `role-playbook.md`, `agent-reliability.md`). A result that cannot name its eval is not a result.
4. **Experiment loop.** Runs through the dev-workflow funnel (choice tournaments for method candidates, comparable variants, the environment ladder for anything product-touching); every run one-lined into the project record — question, config, result, verdict, next.
5. **Analysis + honest verdict.** Verified vs judged labels on every claim; negative results are results and are recorded as such.
6. **Readout.** The stage-event artifact (design doc, results readout, demo) riding the team's ceremonies — the research is finished when its claim is communicated and landed per the lifecycle's landing bar, not when the experiments stop.

**Provenance discipline (binding):** every named method states on first mention whether it is established practice/literature (with source) or this effort's own proposal; provenance is checked against the source before being asserted.

## Auto-research jobs

Canonical home: `auto_research.md` — the lane's standing jobs (literature and internal prior-art scouts, eval-landscape watch, experiment monitor, analysis/writing assists) and the candidate funnel, executed by the platform (`autoflow.md`) as registry entries (`work-engine.md`).

## Fit with the rest

A research effort IS a project: it lives on the portfolio board, competes in prioritization, and lands explicitly. What this module adds is the arc's research-specific stages (question/grounding/hypothesis rigor) and the standing jobs; everything else — selection, negotiation, sync cadence, landing — is the lifecycle's, unchanged.
