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

## generalize-at-settle

Trigger: a point just settled somewhere local (one project's convention, one register's rule, one fix) and plausibly applies more widely — or a second surface is found hand-rolling what a first already solved.

1. Ask the two axes. SCOPE: does the point belong higher up the estate's ladder (project note → hub/estate-wide convention)? PARALLELS: which analogous surfaces (other projects, registers, checklists) should carry the same point — including parallels nobody has named yet?
2. Sweep the named parallels and apply the point there in the same sitting; a parallel deliberately skipped gets a one-line named reason.
3. A promotion up a level lands via capture-at-settle (`session-discipline.md`): written durably, consumer named, old world swept.
4. The work-side ladder tops out at the estate's own hub conventions: the seed is never edited from the work side (one-way flow). A point that looks corpus-worthy is noted as a candidate in the hub's conventions and travels upstream only through the maintainer.

## review-simplify pass

Trigger: a change is functionally complete, before merge.

1. Sweep the diff for reuse and simplification: dead code, duplicated logic, missed reuse of existing helpers, needless abstraction.
2. Check naming, idiom, and comment density match the surrounding code.
3. Separately hunt bugs: edge cases, error paths, concurrency, off-by-ones.
4. Apply mechanical fixes directly; raise behavior-changing findings for discussion.

## audit-instructions

Trigger: periodic, or when an instruction surface visibly misfires (references a dead file, never fires when it should, overlaps another).

1. Roster all instruction surfaces (always-loaded files, skills, checklists); verify their references still exist.
2. Mine recent usage: did each fire, did it help, was it corrected.
3. Propose per item: refine / merge / retire. Mechanical fixes apply directly; behavior-changing rewrites get approval.
4. After any rename/retirement of a standard or tool: grep all instruction surfaces for the old world and fix stale references in the same session.

## audit-law

Trigger: periodic; when two law/knowledge surfaces contradict each other; and always after the unfold regenerates local adaptations.

1. Roster the law and knowledge surfaces: binding rules and conventions (the committed corpus is canonical), unfold-generated local adaptations, knowledge digests, agent instruction files.
2. Deterministic pass first: referenced files and sections still exist; dated items that came due; every adapted copy names the canonical it derives from.
3. Judgment sweep for drift: superseded-but-still-active phrasing, canonical-vs-adaptation divergence, a rule stated in two places with no declared master.
4. On conflict the canonical wins: fix the copy, never fork the rule. Mechanical fixes apply directly; rule rewrites get approval.

## audit-conversations

Trigger: periodic, or after a stretch of sessions that felt rough.

1. Gather whatever recent agent-conversation history the sanctioned tooling exposes (transcripts, logs, chat history). If it exposes none, collect the user's reported pain points instead.
2. Scan for the user's own frustration and correction signals: emphatic punctuation runs, repeated corrections, "I already said" moments.
3. Judge each moment: what frustrated the user, did the working system cause it, what root fix prevents recurrence.
4. Route each accepted fix to its proper form (rule, procedure, check, tooling); log system-caused moments as failure-capture rows. Mechanical fixes apply directly; behavior-changing rewrites get approval.

## audit-structure

Trigger: evidence-driven only, never cadence: symptoms recurring across prior audits that point at a container rather than its content (items with no clear home, the same content moved twice, a file grown past its stated purpose).

1. Roster the containers: folder layout, module boundaries, the task convention, state files.
2. For each recurring symptom, ask whether the container's shape (not the content) caused it.
3. Every finding is propose-first, and structural moves are information-lossless: move, never delete.

## audit-tools

Trigger: periodic, or a tool/automation visibly limping without being an incident.

1. Roster the tools and automations in use (editor and agent wiring, scripts, hooks, scheduled jobs), each with its evidence trail: logs, stamps, last outputs.
2. Verify each is alive and earning its keep: when it last ran, when it last produced something useful, whether failure rows cite it.
3. Propose per item: keep / fix / retire. For a candidate NEW tool, recommend a bounded trial: capped, quittable, with a named keep-or-quit checkpoint.

## failure-capture

Trigger: the user corrects the agent's work or labels something a failure; a shipped change regresses; any defect worth remembering. Runs in the same session as the incident:

1. Fix the live work first. The record never substitutes for the fix.
2. Log one row in a local failures ledger (a plain gitignored file under the workspace's local state): date · what happened in one line · cause class (instruction gap / verification gap / tooling / process / packaging of a human-executed step) · severity band (low / med / high).
3. If the same failure class already has a written rule, a second occurrence escalates the fix from rule text to enforcement (a check, a hook, a pipeline stage), never a third restatement.

## audit-failures

Trigger: periodic, or when deciding what to fix first in how the working system itself runs.

1. Aggregate the failure-capture rows by cause class, weighted by severity, never raw counts.
2. For the top classes, decide leave vs fix. A fix targets the root (the instruction surface, the tool, the gate), not the symptom.
3. This ledger is the outcome record the human-agent boundary rule reads (see `human-agent-collaboration.md`): a measured failure deficit adds a gate or check back; a clean record supports removing one.

## improvement-loop dispatch

The audits above form ONE family over the working system's estates: procedures (audit-instructions) · law and knowledge (audit-law) · lived experience (audit-conversations) · structures (audit-structure) · tools (audit-tools) · failures (failure-capture feeding audit-failures). "Optimize everything" means: run whichever members are due, then consolidate every proposal into ONE approval batch, never a drip of asks. The loop optimizes the working SYSTEM; the work content itself is governed by its own plans and reviews. The settle-time WRITE transforms — capture-at-settle (`session-discipline.md`) · workflow-extraction · generalize-at-settle — are the same loop's write phase: the audits correct what the settle moments failed to capture.

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
2. Check the calendar and inbox for anything that reorders today (work-sanctioned surfaces only) — the inbox check IS the triage sweep of `communication-flow.md` (three lanes, drafts staged inert), never a parallel hand-rolled pass; the calendar read also feeds that module's meeting-prep assist.
3. Name the day's one or two priorities out of the ordered list; surface only what needs action or eyes — nothing-due checks stay silent.

## terminal-recovery

Trigger: new terminals fail to open (spawn errors such as `posix_spawnp failed`, "native exception", or silent failure), in the editor or machine-wide.

1. Diagnose before restarting anything. On macOS the usual cause is pty exhaustion — the kernel's pseudo-terminal pool (~511) is used up: count live ptys (`ls /dev/ttys* | wc -l`) and list the top holders (`lsof | grep ttys`, grouped by process). Electron-family editors (VS Code, Cursor) are known slow leakers via integrated terminals that don't release ptys on close. On a Windows device the analogue (ConPTY/handle leaks) has different diagnostics — re-derive on first occurrence and record it here.
2. Separate leaked/orphaned holders from live working sessions — a process's age alone doesn't make it dead.
3. Drain at the source: close the leaking app's integrated terminals or restart the app itself, rather than killing processes blind.
4. Gate: a person's live working sessions (agent sessions, editors, shells holding open work) are never killed on the system's initiative, however stale they look — present the list (pid · what it is · age) and wait for an explicit yes.
5. After recovery, verify new terminals spawn, then restore any sessions the drain took down (see session-restore).

## session-restore

Trigger: working sessions (agent CLI sessions, editor windows) were closed by a reboot, power loss, editor force-quit/crash, or a cleanup — and the working state should come back.

1. Reconstruct the victim list from evidence — the agent CLI's session logs, process history, workspace state — never from memory.
2. Restore each session in its own project workspace, using the agent CLI's native resume mechanism (verify what the sanctioned CLI supports on device before relying on it).
3. Restore is on-demand and human-triggered only. An always-running auto-resume watcher is a known failure shape — it fires on windows a person closed by hand and types into whatever has focus; don't build one.
4. A hand-closed session is a decision, not a casualty: restore only what the crash took.
