# Portable skills (shortlist)

Recurring procedures worth materializing on the work side, in whatever form the sanctioned tooling supports — agent skills, instructions files, or plain printed checklists. Each entry: trigger, the FULL procedure the work will use (never a compressed sketch that forces re-derivation), human gates. The unfold adapts the format; the procedures are tooling-agnostic.

## systematic-debugging

Trigger: any bug, crash, failed run, or wrong/suspicious result — BEFORE proposing any fix.

1. Reproduce first; capture the exact failing command and output.
2. State expected vs observed behavior, one sentence each.
3. Form a hypothesis; pick the cheapest observation that would falsify it; iterate until the root cause is identified with evidence.
4. Only then fix — at the root cause, never the symptom.
5. Verify the fix against the original reproduction; check for siblings of the same defect elsewhere.

Anti-pattern this exists to prevent: guess-and-patch loops ("try changing X and see") without a diagnosis.

## results-triage

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

## generalize

Trigger: a point just settled somewhere local (one project's convention, one register's rule, one fix) and plausibly applies more widely — or a second surface is found hand-rolling what a first already solved.

1. Ask the two axes. SCOPE: does the point belong higher up the estate's ladder (project note → hub/estate-wide convention)? PARALLELS: which analogous surfaces (other projects, registers, checklists) should carry the same point — including parallels nobody has named yet?
2. Sweep the named parallels and apply the point there in the same sitting; a parallel deliberately skipped gets a one-line named reason.
3. A promotion up a level lands via capture-at-settle (`session-discipline.md`): written durably, consumer named, old world swept.
4. The work-side ladder tops out at the estate's own hub conventions: the seed is never edited from the work side (one-way flow). A point that looks corpus-worthy is noted as a candidate in the hub's conventions and travels upstream only through the maintainer.

## project-founding

Trigger: a container is about to be created — a per-project home under main-work at an ACCEPT or an accepted initiative (`project-lifecycle.md` stages 3/5), a new function project when a standing kind of work settles with no home, or an infrastructure charter's founding gate firing at its named first consumer. Also fires on discovery of homeless work: real work accumulating in sessions, scratch, or another project's files with no registered home.

0. **Size test first — don't over-found.** A single deliverable is a task line; a multi-move arc with a named end is a campaign folder inside its owning project (`estate-structure.md`); only STANDING work — no natural end, its own state, its own claim on attention — earns a project.
1. **Classify the kind** (`estate-structure.md` kinds roster): per-project home under main-work (product work) · function project (a standing register/record of the job) · infrastructure (a seam ≥2 projects ride). Infrastructure founds ONLY at its charter's named consumer gate, per its own module (`store.md` · `finder.md` · `messages.md` · `llm_utils.md` · `devices.md` · `autoflow.md` · `auto_research.md`); a capability two projects both need but no charter covers is infrastructure debt — flag it at the hub, never hand-roll it inside one project.
2. **Settle name and home.** Name: short, or long only because accuracy needs every word (`session-discipline.md` naming rule). Home: a directory under the estate's A4 root per the registry's layout — per-project homes under main-work, function and infrastructure projects as siblings. The employer's systems stay canonical for what they own (code in the employer's git, team docs in the team's doc system — the placement map): the estate home holds the project's RECORD and state, never a duplicate of a team surface.
3. **Seed the task surfaces** (`task-convention.md`): `TODO.md` headed `# TODO (ordered)`, `NOW.md`, `archive.md`. An existing file is NEVER overwritten — founding over existing material is absorption (step 8).
4. **Seed the kind-specific state.** Per-project home: the project record per `dev-workflow.md` — the team's design-doc/status convention where one exists, else `local/state/projects/<name>.md` — and the accept's premortem (`risk-register.md`) declared before work starts. Function project: its registers per its owning corpus module, in the data shape (`estate-structure.md`): typed entries · append-only dated assessments · machine estimates separate from the user's judgments · knobs in a config block. Infrastructure: per its charter module. Deliberately NOT pre-seeded: `lessons.md` and `handbook.md` found lazily at their first entry — empty shells are clutter.
5. **Instructions layer:** a per-project instructions file in the sanctioned tooling's format, stating this project's own scope and citing the hub's law — never copying it.
6. **Register — the step that makes the project exist.** One estate-registry row at the hub: name · kind · home path · state files · genome modules (which corpus modules govern it) · EDGES (`consumes:` infrastructure seams · `feeds:` where outputs flow); state crosses the project's boundary only via the crossing protocol's four forms. Same sitting, each where it applies: a portfolio-board line for product projects (`name · stage · sponsor · why-it-matters · next action · next-show`, `project-lifecycle.md`) · a placement-map row for any NEW content kind the project introduces (`estate-structure.md`) · any standing job into the engine registry (`agent-jobs.yaml`, the job writing this project's own state, `work-engine.md`) · a footprint-register line for any personal credential or sign-in the founding lands (`device-return.md`).
7. **First task:** the project's TODO opens with its first concrete action — a project founded with an empty TODO is a zombie at birth.
8. **Absorption:** work already accumulated elsewhere MOVES whole into the new home — information-lossless, move never delete; an old location keeps a pointer only where something still routes readers there. Duplicated content collapses to one home plus pointers.

Gates: founding a NEW function project or infrastructure seam is a structure decision — the user's word first; a per-project home rides the accept decision itself, no second ask. Absorption that rewrites or removes another project's files: propose first.

Anti-patterns this exists to prevent: work accumulating with no registered home; pre-seeding homes for candidates not yet accepted (the board tracks candidates; homes found at accept); a project created but never registered — invisible to the attention view and every audit.

## dig

Trigger: a project needs a SCOPED discovery — one question, a bounded sweep for candidates (people worth knowing for a named goal, internal events in a window, teams or projects touching a topic, transfer/program opportunities) — bigger than one query, smaller than a standing watch.

1. The commissioning project writes a dig BRIEF: the question, the candidate shape (entity kind + fields per the store's schema), scope bounds, and what "worth surfacing" means — the scoring config stays with the commissioning project.
2. The dig runs through the finder (`finder.md`), across every channel the roster reaches; per-dig hand-rolled channel access is the same defect as ever.
3. Candidates land as typed store entries (`store.md`) with evidence pointers; scoring runs in the store per the brief; the commissioning project judges the shortlist.
4. The dig CLOSES — report, shortlist, what was not covered. Anything continuing becomes a standing watch (engine job) by explicit decision, never by drift.

Anti-pattern this exists to prevent: every project hand-rolling its own funnel over the same channels.

## review-simplify

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
Since v3 its evidence includes the hub's registry GRAPH: kinds, consumes/feeds edges vs reality, crossing-protocol violations (state written across a boundary outside the four legal forms), unregistered containers.

## audit-tools

Trigger: periodic, or a tool/automation visibly limping without being an incident.

1. Roster the tools and automations in use (editor and agent wiring, scripts, hooks, scheduled jobs), each with its evidence trail: logs, stamps, last outputs.
2. Verify each is alive and earning its keep: when it last ran, when it last produced something useful, whether failure rows cite it.
3. Propose per item: keep / fix / retire. For a candidate NEW tool, recommend a bounded trial: capped, quittable, with a named keep-or-quit checkpoint.
Since v3 the roster includes the infrastructure trio's adapters (store engine, finder sources, messages channels) and the seed's registry row — flag a stale update channel (newest version seen far ahead of installed, or last-checked ancient).

## audit-overlap

Trigger: periodic, or on suspicion that the same logic lives in two places ("is this duplicated somewhere", structures that feel half-replaced by something newer).

1. Collect deterministically first, across the estate's own code and doc surfaces: dead/unused code (linter dead-code passes), unused dependencies, copy-paste clones, duplicate symbol names, residue name patterns (`*_old`, `*_v1`, `*_backup`, `copy`), and things a newer thing visibly superseded (version-control history shows the replacement landing while the old form stayed).
2. Give every finding a reasoned verdict: **keep** (good overlap — record why, so it never re-surfaces) · **sweep** (residue — delete, lossless via version control) · **merge** (live duplication — extract to ONE home, consumers cite it; a capability two projects both need is infrastructure debt, `estate-structure.md`).
3. Rank by weight — a duplicated seam or core module outranks a duplicated script or doc — never by raw count.
4. Sweeps and mechanical merges apply directly; merges that change a consumer-facing surface get approval. Employer-owned repos are out of scope: this audits the estate's own surfaces; team code follows the team's own review channels.

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

The audits above form ONE family over the working system's estates: procedures (audit-instructions) · law and knowledge (audit-law) · lived experience (audit-conversations) · structures (audit-structure) · tools (audit-tools) · code overlap (audit-overlap) · failures (failure-capture feeding audit-failures). "Optimize everything" means: run whichever members are due, then consolidate every proposal into ONE approval batch, never a drip of asks. The loop optimizes the working SYSTEM; the work content itself is governed by its own plans and reviews. The settle-time WRITE transforms — capture-at-settle (`session-discipline.md`) · workflow-extraction · generalize — are the same loop's write phase: the audits correct what the settle moments failed to capture.

## error-analysis

Trigger: every 2–4 weeks on an LLM feature, and after any significant model/prompt change or incident. (Backing conventions: `role-playbook.md`.)

1. Sample 100+ fresh traces, weighted toward outliers (latency spikes, retries, auto-flagged, user-reported).
2. Open coding: free-text annotate what went wrong, no predefined categories. A human does the first 30–50 before any LLM assistance; never outsourced.
3. Axial coding: cluster annotations into a named failure taxonomy with per-category frequency.
4. Stop at saturation: ~20 consecutive traces revealing no new category.
5. Build or update evaluators only for observed failure modes, cheapest form first (assertion → reference-check → LLM-judge).
6. Re-check judge calibration against a refreshed human-labeled sample.

Anti-pattern this exists to prevent: trusting aggregate eval scores while the failure taxonomy silently rots.

## judge-calibration

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

## day-start

Trigger: start of a working day or a cold return to the workspace.

1. Read the session board (`NOW.md`) and the TODO head.
2. Check the calendar and inbox for anything that reorders today (work-sanctioned surfaces only) — the inbox check IS the triage sweep of `messages.md` (three lanes, drafts staged inert), never a parallel hand-rolled pass; the calendar read also feeds that module's meeting-prep assist, and its meeting list opens with the start-capture-before-entering front line (`messages.md` §Meetings capture bullet).
3. Deliver as ONE page in the board form (`human-agent-collaboration.md` §The board delivery form): a headline sentence naming the day's one or two priorities, then the boards in placement-test order. Surface only what needs action or eyes — nothing-due checks stay silent.

## event-prep

Trigger: a consequential meeting on the calendar (a 1:1, a review, any meeting where something is decided or asked — routine standups need none), or a committed work event (offsite, conference, org all-hands, team social). Two grades by shape; both serve the one convention: entered prepared, left recorded (`messages.md` §Meetings).

**Meeting grade** — the short prep note in the owning project (the meeting-prep assist drafts it where the engine runs; else it rides day-start's calendar read):

1. What it is: the meeting's purpose in one line; each attendee one line (role + what they own here), from the employer's own surfaces (directory/org chart, team pages, recent threads) — never assume the user holds the roster in their head.
2. Desired outcome first: what result makes the meeting a success; then the user's asks, each carrying its context and a recommendation (the recipient-attention rule, `messages.md`).
3. Expected questions with prepared answers, drafted from the project record and worklog; where the user presents, the narrative skeleton per `communication-craft.md`.
4. Exit: the prep note pre-names where each expected outcome will land (worklog daily line, project record, company log), so the post-meeting capture is a fill-in, never a reconstruction.

**Event grade** — a full brief, built the day before, exactly four sections:

1. **What it is** — format and purpose of the event, hosts/organizers one line each, expected attendance and composition. Never assume the user knows the event class or the organizations.
2. **Attending** — ONE time-ordered logistics table; every fixed fact lives at its step, never as separate bullets: getting there, entry requirements (badge/registration/code), agenda and session choices, a brief re-read slot shortly before leaving. A gated field (venue, entry code, approval) may hold a placeholder ONLY together with a wake mechanism filed in the same sitting — a dated TODO watch whose check step sweeps the registration mailbox and completes the placeholder rows IN PLACE. An event-day brief with a placeholder address is a defect.
3. **Targets** — opens with the aim (what outcome makes attendance worth the time; the attendance read per `career.md` growth events), then the ranked people to seek — from a real attendee/speaker list where one exists, never guessed — each with a hook and an on-site finding note. Organizers rank high by default: the relationship compounds.
4. **Strategies** — the intro line (lead with what that room values), per-target ask scripts, the on-site finding plan in numbered steps, and the after-event close: outcomes recorded per the meetings convention, follow-ups staged as drafts (`messages.md`).

Both grades: the system does the doable prep itself (pull the records, draft the note, stage anything fillable) rather than listing it as the user's homework — the user's steps are only what genuinely needs their presence. Every checked fact carries source + checked-date; times and logistics re-verify on prep day. Execute-ready to the final target: a brief that names WHO or WHAT without HOW is incomplete.

## terminal-recovery

Trigger: new terminals fail to open (spawn errors such as `posix_spawnp failed`, "native exception", or silent failure), in the editor or machine-wide.

1. Diagnose before restarting anything. On macOS the usual cause is pty exhaustion — the kernel's pseudo-terminal pool (~511) is used up: count live ptys (`ls /dev/ttys* | wc -l`) and list the top holders (`lsof | grep ttys`, grouped by process). Electron-family editors (VS Code, Cursor) are known slow leakers via integrated terminals that don't release ptys on close. On a Windows device the analogue (ConPTY/handle leaks) has different diagnostics — re-derive on first occurrence and record it here.
2. Separate leaked/orphaned holders from live working sessions — a process's age alone doesn't make it dead.
3. Drain at the source: close the leaking app's integrated terminals or restart the app itself, rather than killing processes blind.
4. Gate: a person's live working sessions (agent sessions, editors, shells holding open work) are outside the drill entirely, however stale they look — the system neither kills them NOR proposes, packages, or paste-readies a kill list of them; the only trigger for closing one is the person's own explicit ask naming it. Drain at the leak source only (step 3). (Seed incident class: a proposed "stale sessions" kill list closed dozens of open sessions and freed zero terminals — the stale-looking sessions were not the leak.)
5. After recovery, verify new terminals spawn, then restore any sessions the drain took down (see session-restore).

## session-restore

Trigger: working sessions (agent CLI sessions, editor windows) were closed by a reboot, power loss, editor force-quit/crash, or a cleanup — and the working state should come back.

1. Reconstruct the victim list from evidence — the agent CLI's session logs, process history, workspace state — never from memory.
2. Restore each session in its own project workspace, using the agent CLI's native resume mechanism (verify what the sanctioned CLI supports on device before relying on it).
3. Restore is on-demand and human-triggered only. An always-running auto-resume watcher is a known failure shape — it fires on windows a person closed by hand and types into whatever has focus; don't build one.
4. A hand-closed session is a decision, not a casualty: restore only what the crash took.
