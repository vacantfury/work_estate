# Changelog

All notable seed changes, one entry per version. Versions are SemVer git tags: MAJOR = a convention reversed or restructured (existing derived layers must regenerate), MINOR = additive (new modules or module sections), PATCH = wording or fix. Each entry names the changed modules and the derived layers they affect — this file is the manifest the update mode (`UNFOLD.md` §Updating an installed estate) reads against the installed version.

## [Unreleased]

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
