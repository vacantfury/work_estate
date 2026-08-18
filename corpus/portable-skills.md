# Portable skills (shortlist)

Recurring procedures worth materializing on the work side, in whatever form the sanctioned tooling supports — agent skills, instructions files, or plain printed checklists. Each entry: trigger, compact procedure, human gates. The unfold adapts the format; the procedures are tooling-agnostic.

## systematic-debugging

Trigger: any bug, crash, failed run, or wrong/suspicious result — BEFORE proposing any fix.

1. Reproduce first; capture the exact failing command and output.
2. State expected vs observed behavior, one sentence each.
3. Form a hypothesis; pick the cheapest observation that would falsify it; iterate until the root cause is identified with evidence.
4. Only then fix — at the root cause, never the symptom.
5. Verify the fix against the original reproduction; check for siblings of the same defect elsewhere.

Anti-pattern this exists to prevent: guess-and-patch loops ("try changing X and see") without a diagnosis.

## experiment-results-triage

Trigger: a finished (or failed) experiment/job run, before any metric is trusted or recorded.

1. Scan job logs for errors and warnings first.
2. Sanity-check headline metrics against expectations; flag implausible values.
3. Spot-check raw outputs for outliers and degenerate cases.
4. Identify logic-invalid runs (wrong config, contaminated data) and exclude them with a recorded reason.
5. Record verified results in the project's results doc.

Gates: destructive cleanup of run artifacts and edits to the results doc get explicit approval.

## workflow-extraction

Trigger: a multi-step workflow has just recurred, with articulated preferences and decision points ("every time we do this…").

1. Capture the target, the corrections given along the way, and the actual path taken.
2. Distill the reusable stages, decision points, and human gates.
3. Route each piece to its proper form — code / skill / rule / state file (see session-discipline, form selection).
4. Write it durably in the same session; new automation installs only with approval.

## review-simplify pass

Trigger: a change is functionally complete, before merge.

1. Sweep the diff for reuse and simplification: dead code, duplicated logic, missed reuse of existing helpers, needless abstraction.
2. Check naming, idiom, and comment density match the surrounding code.
3. Separately hunt bugs: edge cases, error paths, concurrency, off-by-ones.
4. Apply mechanical fixes directly; raise behavior-changing findings for discussion.

## instructions-audit

Trigger: periodic, or when an instruction surface visibly misfires (references a dead file, never fires when it should, overlaps another).

1. Roster all instruction surfaces (always-loaded files, skills, checklists); verify their references still exist.
2. Mine recent usage: did each fire, did it help, was it corrected.
3. Propose per item: refine / merge / retire. Mechanical fixes apply directly; behavior-changing rewrites get approval.
4. After any rename/retirement of a standard or tool: grep all instruction surfaces for the old world and fix stale references in the same session.

## error-analysis-pass

Trigger: every 2–4 weeks on an LLM feature, and after any significant model/prompt change or incident. (Backing conventions: `role-playbook.md`.)

1. Sample 100+ fresh traces, weighted toward outliers (latency spikes, retries, auto-flagged, user-reported).
2. Open coding: free-text annotate what went wrong, no predefined categories. A human does the first 30–50 before any LLM assistance; never outsourced.
3. Axial coding: cluster annotations into a named failure taxonomy with per-category frequency.
4. Stop at saturation: ~20 consecutive traces revealing no new category.
5. Build or update evaluators only for observed failure modes, cheapest form first (assertion → reference-check → LLM-judge).
6. Re-check judge calibration against a refreshed human-labeled sample.

Anti-pattern this exists to prevent: trusting aggregate eval scores while the failure taxonomy silently rots.

## llm-judge-calibration

Trigger: a new LLM-judge evaluator, or the maintenance cadence of an existing one.

1. Assemble 100+ human-labeled examples with written critiques from the principal domain expert; binary pass/fail, not Likert.
2. Iterate the judge prompt against those labels; measure TPR/TNR and inter-rater agreement (Cohen's Kappa) on a held-out split — benchmark expectations against human-human agreement, don't demand the judge beat noisy ground truth.
3. Pairwise judgments: run twice with swapped order to cancel position bias; control for length bias.
4. Give the judge an "Unknown" escape hatch; grade each rubric dimension separately.
5. Develop with the most capable model available first; cost-optimize only after alignment is established.
6. Judges are not set-and-forget — re-calibrate on cadence and after any model change.

## experiment-readout

Trigger: an online experiment/flight reaches its readout point (or is stopped early by a guardrail).

1. Restate the hypothesis, variants, and the metrics as declared BEFORE launch (primary / secondary / guardrail) — no post-hoc metric shopping.
2. Report primary and secondary results with uncertainty; check guardrails as hard constraints.
3. Check tail behavior (quantiles), not just averages; note any variance surprises from model changes.
4. Close with an explicit ship / hold / kill recommendation and what changed since the previous version.
5. Record the readout durably where the team keeps experiment history.

## day-start orientation

Trigger: start of a working day or a cold return to the workspace.

1. Read the session board (`NOW.md`) and the TODO head.
2. Check the calendar and inbox for anything that reorders today (work-sanctioned surfaces only).
3. Name the day's one or two priorities out of the ordered list; surface only what needs action or eyes — nothing-due checks stay silent.
