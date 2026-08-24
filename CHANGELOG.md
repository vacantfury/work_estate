# Changelog

All notable seed changes, one entry per version. Versions are SemVer git tags: MAJOR = a convention reversed or restructured (existing derived layers must regenerate), MINOR = additive (new modules or module sections), PATCH = wording or fix. Each entry names the changed modules and the derived layers they affect — this file is the manifest the update mode (`UNFOLD.md` §Updating an installed estate) reads against the installed version.

## [Unreleased]

## [3.3.0] - 2026-08-24

Law-sync pass (second of its kind; baseline was the 2026-08-19 axis-1 refresh): the maintainer's working-rule estate walked rule by rule against the corpus, every rule settled or amended since the baseline either ported in the seed's generic voice or skipped with a named reason. One real drift fixed.

- Changed (drift fix): `portable-skills.md` **terminal-recovery** step 4 — live working sessions are outside the drill entirely: the system neither kills them nor proposes/packages a kill list of them; only the person's own explicit ask naming a session triggers a close (supersedes the present-list-and-wait shape; seed incident class: a proposed stale-sessions kill list closed dozens of open sessions and freed zero terminals).
- Added: `session-discipline.md` — plans are ordered steps, dates only on real deadlines · no self-initiated postponement (timing risks named, never acted on; time-sequencing is the user's call) · tool-path order (programmatic seam before UI automation before human hands; self-repair before a human ask) · strong dissatisfaction handled as a defect report (diagnose-and-fix, stand ground with evidence, no apology paragraphs) · mid-session standing orders persist (restate at receipt, park durably, re-list after context compaction) · form-stamp on proposals + founding-is-three-lookups.
- Added: `task-convention.md` — grasp the big, release the small (selection AND sequence) · items cited by position never by id, with the store-flip rule (generated TODO view, ids as tooling addresses only, hand-edits ingest as input).
- Added: `engineering-standards.md` — the categorical twin (closed vocabularies carry a typed `unknown`/`other` residual failing toward attention, plus a revision signal) · §Size to the known end-state (general form by default; narrow-first needs a named concrete risk).
- Added: `communication-craft.md` rule 4 — plain, separate sentences in drafted prose; no dash-line clause connectors; compound-word hyphens fine.
- Added: `messages.md` drafts — polite AND concise register (warmth by register, never length) · the recipient's attention as a deliberately-spent cost (batched asks, one decision per ask with recommendation, never re-ask).
- Added: `boundary-protocol.md` §User-only zones — a directory named `ai_agent_proof` is a hard agent-excluded wall anywhere in the user's estate.
- Added: `estate-structure.md` §The law layer — one canonical home per rule, cite-never-copy, tiered delivery, the record-per-rule + generated-view form when hub law outgrows one file, current-rule-only maintenance.
- Added: `portable-skills.md` **audit-overlap** (deterministic collection → keep/sweep/merge verdicts → weight-ranked; estate surfaces only) + dispatch-note family row.
- Added: `llm_utils.md` — default provider is the sanctioned agent tooling's own account; separately-billed API routes are a deliberate per-consumer config choice.
- Skipped with named reasons (recorded here so the check never re-runs from scratch): personal-data-routing and jurisdiction rules (the user's own estate's affair; no personal corpus here) · person-model/evidence rails beyond the people cards (people.md + messages routing already carry the work-grain duty) · deployed-system watchdog standard (work-engine autonomy-gradient axis 3 already carries it) · chat status-footer/manifest conventions (session idiom, not portable convention) · owner-figure strategy rules (land in the self-model's standing rules at unfold, per that module).
- Affects: regenerate derived layers of session-discipline, task-convention, engineering-standards, communication-craft, messages, boundary-protocol, estate-structure, llm_utils; materialize the audit-overlap hub skill. No living state touched.

## [3.2.0] - 2026-08-24

- Added: `portable-skills.md` **project-founding** — the full founding procedure for any new estate container, in one entry (user decision 2026-08-24: full form, everything the founding uses): size test (task / campaign / project) → kind classification (per-project home · function project · infrastructure at its charter gate) → name + home (employer systems stay canonical for what they own) → task surfaces per `task-convention.md` → kind-specific state (project record + premortem / registers in the data shape / charter module; lessons + handbook stay lazy) → per-project instructions file citing hub law → the registration sitting (estate-registry row with edges · board line · placement-map rows · engine jobs · footprint lines) → first task → absorption (move whole, never delete). Gates: a new function project or infrastructure seam takes the user's word; a per-project home rides the accept itself. Anti-patterns: homeless work, pre-seeded candidates, unregistered projects.
- Changed: `portable-skills.md` house rule (user correction 2026-08-24) — each entry carries the FULL procedure the work will use, never a compressed sketch that forces re-derivation; README row aligned. `project-lifecycle.md` stage-3 accept and `UNFOLD.md` Phase 3 step 11 now cite the procedure.
- Affects: materialize one new hub skill in the skills layer; no living state touched.

## [3.1.0] - 2026-08-24

The infrastructure quartet (user decisions 2026-08-24): the work-stack infrastructure ported at end-state as independent projects, names kept exact from the maintainer's proven layering. Governing insight: incumbents (gateways, clusters, the sanctioned agent tooling) are SUBSTRATE that sits behind these seams — they never replace the estate's own seam, client, platform, and engine layers.

- Added: `corpus/llm_utils.md` — the LLM provider seam: one seam, sanctioned providers behind it, usage ledger; incumbent-vs-build resolved at intake; founds at the first code consumer.
- Added: `corpus/devices.md` — the compute and device client: registry single-truth, dispatch seam, run state, device runbooks; founds at the first granted compute target.
- Added: `corpus/autoflow.md` — the automation platform executing the engine's job registry: scheduler, cycle runtime, worker dispatch, run ledger, liveness; the cycle-pattern and runtime-adaptation text moved here from `work-engine.md`; founds at the first sanctioned scheduled job.
- Added: `corpus/auto_research.md` — the autonomous research engine: the standing jobs (moved here from `research-workflow.md`) plus the candidate funnel (generate → vet → package); the funnel never founds a bet — the user and their manager are the gate.
- Changed: `estate-structure.md` — Kinds roster (infrastructure grows to seven); not-ported list amended (scheduler clause scoped: the platform runs THROUGH the sanctioned tooling, never beside it; quartet porting recorded); self-audit gains the estate-wide backup-verified check (whole estate per A6, route restore-tested at least once, unresolved A6 re-surfaced).
- Changed: `research-infrastructure.md` work-stack bullet re-points to the two charters; `work-engine.md` and `research-workflow.md` carry pointers where text moved; README rows added.
- Affects: the hub estate registry gains four rows (kind: infrastructure, state: chartered until each founding gate fires); regenerate derived layers of work-engine, research-workflow, research-infrastructure, estate-structure. No living state touched.

## [3.0.0] - 2026-08-24

The v3 clear structure (user review sittings, design principle 26). MAJOR: roster restructured.

- Roster: hub · store · finder · messages (infrastructure trio) · people · worklog · benefits · career · health · risk · research · main-work. Cut by content kind: information (finder) · person-traffic (messages) · relationships incl. threads (people).
- Renamed modules: search→finder (knowledge surfaces only) · communication-flow→messages (owns mail/chat/calendar adapters; routing rules + drafts registry as state) · connections→people · resources→benefits (money-like claims only) · performance→career (absorbs growth + positioning; scope = this company only).
- Dissolved: the company project — the watch is a standing capture job; signals typed into the store, person-signals → people, themes/reward map → career `themes.md`. Also gone: the short-lived channels concept (each bus owns its own adapters).
- main-work is a real manager project: portfolio board + candidates + accept decisions move OUT of the hub; per-project homes live under it.
- Store: the four scoring folds ported from the proven upstream closed forms — Bayesian **estimate** (normal-conjugate posterior, confidence→precision, half-life decay, mean ± sigma) · **balance** (decayed event account, no Bayes) · **forecast** (odds arithmetic on resolvable claims, Brier-scored) · **bands**; knobs live in the consuming project's config.
- Hub registry gains EDGES (consumes/feeds) — the estate structure GRAPH; the crossing protocol (four legal boundary crossings) lands in estate-structure; audit-structure and audit-tools entries extended to audit the graph, the trio's adapters, and seed staleness.
- Work-engine: ample-budget posture — scarcity machinery dormant where budget is ample (the expected case); spend on depth before speed.
- Migration (user-confirmed at apply): rename module-derived layers; found messages + re-home board into main-work; dissolve company project (data → store/people/career); split resources register into benefits + career growth; rename directories people/benefits/career/main_work; add registry edges; re-answer A8 as two rosters. Register data is moved, never lost.

## [2.2.0] - 2026-08-24

Naming pass (user rule, settled 2026-08-24: a name is either short, or long only when accuracy needs every word — never medium-long and imprecise).

- Changed: skill renames — generalize-at-settle → **generalize** · discovery-dig → **dig** · day-start orientation → **day-start** · experiment-results-triage → **results-triage** · error-analysis-pass → **error-analysis** · llm-judge-calibration → **judge-calibration** · review-simplify pass → **review-simplify**. UNFOLD's update section is now titled **Update**. All live cross-references updated (dated history entries keep the names they recorded).
- Added: the naming rule itself in `session-discipline.md`.
- Affects: regenerate the portable-skills-derived layer under the new names (semantics unchanged); instruction files citing old skill names update at apply.

## [2.1.0] - 2026-08-24

Upstream mimic-check pass (full walk of the maintainer's ecosystem against the roster; mimic unless genuinely different at work).

- Added: portable-skills `discovery-dig` — scoped discovery campaigns any project commissions: brief + scoring meaning stay with the commissioning project, the run rides the search bus, candidates land typed in the store, decided close or explicit promotion to a standing watch. Plus the digs line in `search.md`.
- Added: `estate-structure.md` §Kinds and the dependency rule — steward · infrastructure · function projects · work homes · seed row; one-way dependencies, meaning stays with the owning project, twice-needed capability = infrastructure debt.
- Added: `work-engine.md` cycle pattern (end-state) — user attention batched at cycle boundaries; results reallocate budget.
- Added: two more named absences in the not-ported list — aid-portfolio (people campaigns instead) and urgency runbooks (the employer's incident process governs).
- Fixed: `corpus/README.md` was missing the `store.md` and `search.md` rows (2.0.0 defect).
- Affects: regenerate the derived layers of portable-skills, search, estate-structure, work-engine. No living state touched.

## [2.0.0] - 2026-08-24

Clear-structure restructure (user decisions at the 2026-08-24 structure sitting; design principle 25). MAJOR: a named absence is reversed and the roster is restructured.

- Added: `corpus/store.md` — the estate's typed data + scoring service (schemas per entity kind, scoring configs owned by the projects and executed uniformly, append-only + user-layer protection, registers become views as A7 lands an engine). The data-shape rule is its contract.
- Added: `corpus/search.md` — the retrieval bus: one query seam over the job's many channels (A8 roster, access modes, read-only, standing watches ride it); per-project hand-rolled channel access is a defect.
- Changed: the **communication project is dissolved** — the message/meeting flow stays a convention + engine jobs (it owns no state), the craft lane's state moves under the hub's engine; people is the one person container.
- Changed: renames — **records → worklog**, **company intelligence → company**, **research satellite → research**; UNFOLD Phase 2 gains A7/A8, Phase 3 restructured (infrastructure pair founded right after the hub).
- Migration for an installed estate (apply is user-confirmed, per restructure): (1) found store + search (new step 3; answer A7/A8 into the ledger; registry rows kind: infrastructure); (2) dissolve the communication project — craft state to the hub engine, any person/meeting residue to the people cards and the worklog, remove its registry row; (3) rename the three project directories and update registry rows + instruction files citing old names; (4) regenerate the derived layers of the modules changed here. No register data is lost or moved otherwise.

## [1.3.0] - 2026-08-24

- Added: the seed clone is itself REGISTERED in the hub's estate registry as the estate's one evolving external dependency (kind: seed): clone path · installed version · update-channel state (A2) · last checked · last applied. The update mode's check and apply steps write this row, so the hub traces seed updates and pending ones surface through the ordinary attention view; the check may register as a low-cadence A2-gated engine job, apply always waits for the user.
- Affects: hub founding (UNFOLD Phase 3 step 1) and the update procedure. Installed estates: add the seed row on the first update run (bootstrap line included); no generated layer regenerates, no living state touched.

## [1.2.0] - 2026-08-24

- Added: `corpus/resources.md` — **Events** as the fifth resource kind: internal events are windowed, decided-never-drifted-into; each candidate gets one attendance read per the data-shape rule (learning · visibility · people, against time cost) ending in an attend/skip recommendation; yields route to `company-watch.md` and the people cards.
- Added: `corpus/estate-structure.md` not-ported line now names the shared scoring/discovery-service absence by decision (the data-shape rule carries the scoring discipline in place, in each register).
- Affects: the derived layers of `resources.md` and `estate-structure.md` (wording plus one new register kind; the resources A5 row already covers it — no new row). No living state touched.

## [1.1.1] - 2026-08-24

- Fixed: `portable-skills.md` §day-start orientation step 2 now cites `communication-flow.md` as the one home of the inbox check (the triage sweep; the entry predated that module) — prevents a parallel hand-rolled inbox pass.
- Affects: the portable-skills-derived layer, wording only; no new A5 row, no living state touched.

## [1.1.0] - 2026-08-24

- Added: `corpus/portable-skills.md` §generalize-at-settle — the third settle-time transform alongside capture-at-settle and workflow-extraction: two axes (scope promotion up the estate ladder · parallel sweep across analogous surfaces), applied the same sitting; the work-side ladder tops out at the hub's own conventions, corpus candidates travel upstream only (one-way flow). Plus one write-phase line in §improvement-loop dispatch.
- Affects: the derived instruction/skill layer generated from `portable-skills.md` — one new A5 row (adopt expected; it costs nothing to hold). No other module changed; no living state touched.

## [1.0.0] - 2026-08-24

Baseline release: the full corpus through the 2026-08-20 passes (estate founding, steward-mind hub, autonomy gradient, translation completeness), plus this pass's update machinery.

- Added: versioned delta updates — `UNFOLD.md` §Updating an installed estate (check → delta apply → advance the `HEAD` marker; provenance headers; never a full re-unfold), this `CHANGELOG.md`, design principle 24.
- Affects: no corpus module changed; no derived layer regenerates. The first update run on an installed estate applies only the update convention itself (provenance headers appear lazily as layers next regenerate).
