# Changelog

All notable seed changes, one entry per version. Versions are SemVer git tags: MAJOR = a convention reversed or restructured (existing derived layers must regenerate), MINOR = additive (new modules or module sections), PATCH = wording or fix. Each entry names the changed modules and the derived layers they affect — this file is the manifest the update mode (`UNFOLD.md` §Updating an installed estate) reads against the installed version.

## [6.2.1] - 2026-08-30

- Fixed: **de-identification sweep** (maintainer order 2026-08-30) — hard content rules 1/5 enforced on committed text: the maintainer's code-host account name removed from the 3.4.1 migration line (now a `<account>` placeholder resolved from the clone's existing remote); the author's legal name in `NOTICE.md` replaced with "The author"; a stray auto-seeded catalog file referencing an external system removed (`campaigns/README.md` — it had no valid entries); the repo's former name in rename records reduced to "former name". No convention or module content changes.
- Affects: nothing — no derived layer regenerates; no living state touched. PATCH: content-hygiene fix.

## [6.2.0] - 2026-08-26

- Changed: **`engineering-standards.md` §Prefer mature tools over reinventing — search-first widened to results and to the internal world** (user direction 2026-08-26): before building any capability or attacking any complex problem, search for what already exists — tools AND results (a prior experiment, published measurement, or existing analysis may already answer the question; the search precedes the design, not the review); "existing" spans the open ecosystem AND the employer's internal one — internal libraries, services, platforms, shared repos, other teams' solutions, and internal prior art count as available exactly the way open-source does, and the internal tool wins a tie (owners, support channel, compliance posture already settled).
- Installed-estate migration: none — module text only; no skeleton templates or state files affected.
- Affects: engineering-standards derived layers regenerate. MINOR: additive rule content.

## [6.1.0] - 2026-08-26

- Added: **`estate-structure.md` §Playbooks — the standing conditional form** (settle-time port; the maintainer's practice ratified the form 2026-08-24 and the campaign section had shipped without its standing sibling): one folder + `playbook.md` front door + condition-headed plays; campaign : move :: playbook : play; deliberately-high founding bar (ALL of: standing scope · recurring/unpredictable trigger · cross-firing state · irreducible to a task line or rule · asymmetric cost of late/wrong firing — below the bar it stays a register entry, watch line, or rule); trigger honesty labels (observer + reliability, FRAGILE named), no-regrets first block on event plays with parallel re-verification of stale parameters, settle-only play edits, decided retirement with successor disposition. Boundary kept: employer incidents stay with the employer's incident process. Form template `skeleton/hub/_forms/playbook.md` added beside lessons/handbook/campaign.
- Added: **`risk-register.md` §Seed premortem — role continuity (standing)** (user direction 2026-08-26): two standing entries the ramp seed lacked — role hit by a reorg or layoff (official-channel verification, employer policy knowledge read while calm incl. severance/benefits/internal mobility, work-authorization grace-window awareness, device-return readiness) and performance-management risk (explicit bar restatement confirmed in writing, evidence-based response from the review draft). Scope bounded to this employer plus clean-separation readiness; anything beyond this employer stays off-estate per `career.md`.
- Changed (reference sweep): `corpus/README.md` (estate-structure + risk-register rows) · `skeleton/README.md` (_forms roster) · `skeleton/risk/risks.md` (seed line).
- Installed-estate migration: copy the new form template into `hub/_forms/`; adopt the two role-continuity register entries into `local/state/risks.md` adapted to intake facts.
- Affects: estate-structure and risk-register derived layers regenerate additively. MINOR: additive sections + one new skeleton file.

## [6.0.0] - 2026-08-26

- Added: **`skeleton/` — the installed estate's concrete form, shipped as files** (user decision 2026-08-26, design principle 30). The seed had shipped conventions only; the layout was re-derived at every install. Now the tree itself ships: one directory per roster project (hub · store · finder · ties · worklog · compensation · career · health · risk · research · main-work + the four gated infrastructure dirs), every state file a ready template with its header, sections, and config block written; the estate registry (`skeleton/hub/registry.yaml`, rows + edges + crossing protocol) and the job registry (`skeleton/hub/agent-jobs.yaml`, schema + drafted default jobs) as real schema files; the per-project home template (`skeleton/main-work/_template/`: task surfaces + `record.md`); lazy-founded forms (`skeleton/hub/_forms/`: lessons · handbook · campaign); the clone-ledger template (`skeleton/_clone/ledger.md`, A1–A8 pre-sectioned). Tree drawn once in `skeleton/README.md`; `estate-structure.md` gains §The concrete tree (genome/phenotype split: conventions adapt, structure copies).
- Changed: **`UNFOLD.md` Phase 3 rewritten copy-then-adapt** — new step 0 copies the skeleton (excluding `_clone/`, the gated infrastructure dirs, and `research/` unless intake §18 clears it), deletes A5 fold-aways, strips template headers, adds provenance headers; the remaining steps FILL values instead of inventing structure. §Update step 3: skeleton-instantiated files diff against their template at the installed version; a pre-v6 installed estate gets a one-time conformance offer (add missing files, report divergences) that never moves living state without the user's word per file. Degraded path: the skeleton is hand-copyable with no agent at all. Also fixes drift in "What the unfold creates" (ties, and the §18 gate on research rather than main-work).
- Changed: **seam re-cut of the project modules** — `project-lifecycle.md` RENAMED `corpus/project-pipeline.md` (the module is the pipeline: sourcing → landing); the per-project scaffold and the record split into new **`corpus/project-home.md`** (scaffold, record sections Design/Decision-points/Variants/Rung/Milestones/Landing/Readouts, lifecycle state on the record, founding = copy the template); `dev-workflow.md` §The project record reduced to a pointer; `portable-skills.md` project-founding steps 3–4 become copy-the-scaffold; reference sweep across corpus, `UNFOLD.md`, `CLAUDE.md`, intake (history surfaces keep the old name).
- Changed: **`corpus/README.md` cut to a grouped one-line index** (estate-wide law · hub · infrastructure · function · main-work); each module is its own full statement.
- Changed: **connector naming** (decision made at an installed estate, adopted upstream via the user's relay 2026-08-26): the per-source/per-channel access component is named **connector** (singular kind name), replacing the corpus's "adapter" vocabulary (`ties.md`, `finder.md`, `devices.md`, `llm_utils.md`, `portable-skills.md`, README).
- Fixed: `estate-structure.md` kinds roster still listed the dissolved people project (v4.0.0 leftover).
- Added: the repo's own lifecycle plan, `text_docs/plan.md`.
- Installed-estate migration: at the next update pull, take the conformance offer (skeleton adoption; living state untouched without the user's word); re-point anything citing `corpus/project-lifecycle.md` to `corpus/project-pipeline.md`; apply the connectors → connector rename wherever the estate materialized the old plural name.
- Affects: regenerate derived layers of project-pipeline (né project-lifecycle), dev-workflow, portable-skills (project-founding), estate-structure; new layers from project-home. MAJOR: the install procedure restructured and a module renamed.

## [5.0.0] - 2026-08-25

- Changed: **`messages.md` dissolved into `ties.md` — the single people-and-traffic bus** (user decision 2026-08-25, completing the single-person-home restructure v4.0.0 began). The user's decision covered BOTH modules from the start: one ties module substitutes the people register AND the messages module; v4.0.0 executed only the people half. `corpus/ties.md` now holds the whole human side of the job in one home: the person surface (people read live off the employer's directory, threads, and calendar — no person register, cards, or thread store anywhere in the estate, design principle 29) plus the traffic conventions unchanged in substance (three-lane triage, drafts prepared never sent, waits on the surface itself, meetings entered prepared and left recorded with capture riding the calendar, the three standing jobs). No separate messages module exists.
- Changed (reference sweep): `corpus/README.md` (module row) · `estate-structure.md` (kinds roster; infrastructure absence line) · `finder.md` (bus boundary line) · `human-agent-collaboration.md` (board sources) · `portable-skills.md` (founding module list, day-start step 2, event-prep pointers, update-check roster) · `UNFOLD.md` (A8 roster, skills layer, infrastructure-trio founding step) · `text_docs/design.md` principle 23 record + hub `CLAUDE.md` log line (né annotations).
- Installed-estate migration: the pull itself carries the move (messages.md deleted, ties.md added); re-point any materialized skill/job that cites `corpus/messages.md` to `corpus/ties.md` — job semantics are unchanged, so no `agent-jobs.yaml` rows change beyond the pointer.
- Affects: regenerate derived layers of the former messages module under the ties name (triage sweep, meeting prep assist, post-meeting capture, day-start step 2). MAJOR: a module removed and restructured.

## [4.1.0] - 2026-08-25

- Added: `session-discipline.md` execute-ready bullet gains the **direct-address rule** (user ask 2026-08-25) — anything the person is pointed to (a page, a portal, a document, a file) comes with its direct address: the exact URL or file path, openable as given, on its own line; a described location the person must find by hand is a defect. Re-derived from the maintainer's proven packaging conventions (direct clickable links on documents, direct URLs on hand-offs).
- Affects: regenerate derived layers of session-discipline. No living state touched.

## [4.0.0] - 2026-08-25

- Removed: **`people.md` — the person register and relationship system dissolved** (user decision 2026-08-25, design principle 29). The estate maintains no person register, cards, thread store, or due-lane silence tracking. The employer's own surfaces are the person surface, read live at need: directory/org chart (who someone is, what they own), the mail/chat thread itself (the state of an exchange — an owed reply is visible on the surface the triage sweep already reads), the calendar (touchpoints). One home per kind: a locally maintained person store duplicates surfaces the employer already runs; relationship meaning beyond the job's own surfaces is the user's own affair outside this estate.
- Changed: `messages.md` (§Threads and waits rewritten — the surface is the state; meetings record line and fold-away note drop card routing) · `company-watch.md` (person-signals-to-cards meaning home dropped; the watch's own registers stand, principle 12) · `career.md` (positioning note) · `deliberation.md` (positioning seat grounding) · `estate-structure.md` + `store.md` (example/consumer lists) · `work-engine.md` (Connections lane row removed) · `portable-skills.md` (meeting/event prep reads live surfaces; carding step removed) · `corpus/README.md` (module row removed; messages row) · `UNFOLD.md` (estate list; found-the-people step removed, later steps renumbered; career step).
- Installed-estate migration: remove the people/connections job rows from `agent-jobs.yaml`; deregister the people project from the estate registry; the existing `local/state/people.md` register stops being maintained by the estate — its disposition (delete, or the user keeps a copy outside the estate) is the user's call at the update pass.
- Affects: regenerate derived layers of messages, work-engine, and the meeting/event prep skill materializations. MAJOR: a convention reversed — the people project leaves the roster.

## [3.10.0] - 2026-08-25

- Added: `messages.md` §Meetings **capture-rides-the-calendar bullet** (user decision 2026-08-25) — any rendering of the day's meeting/event calendar (day-start step 2, the meeting-prep assist) OPENS with one standing front line before the meeting lines: start capture before entering. For meetings where the user can — the platform's recording/transcription available and permitted (e.g. Teams/Outlook) — turn it on at entry, then after the meeting open the recording or transcript from the calendar/mail surface and distill it into the record lines; notes by hand where capture isn't available. Placement is the point: a reminder riding only per-meeting prep lines gets missed on the day it matters.
- Changed: `messages.md` standing job **post-meeting capture** now opens the recording/transcript first and distills from it, prompting only for the outcome lines the user alone knows · `portable-skills.md` day-start step 2 carries the front-line reminder on its calendar read · `corpus/README.md` messages line updated.
- Affects: regenerate derived layers of messages and the day-start skill materialization. No living state touched.

## [3.9.0] - 2026-08-25

- Added: `engineering-standards.md` **§Secrets hygiene**, four conventions completing the section's portable core (user decision 2026-08-25): **secret values never appear in output** (no raw environment/process dumps in diagnostics — inherited variables leak that way; a value that reached any output or transcript is exposed: rotate, then fix the leak path) · **agents and automation handle secret names, never values** (injection at launch outside the agent's view; an agent never reads a value back, echoes it, or writes it to a file) · **headless runs authenticate as a machine identity** (the environment's sanctioned service principal / managed identity / service account at least-privilege, created once and reused, credential outside every repo) · **a repo documents the env-var names it needs** (names and shapes, never values — the contract a fresh clone sets up against). Ported and re-derived from the maintainer's proven secrets standard, store specifics stripped; the store-agnostic base (env-var interface, no plaintext values, sanctioned-store-by-intake, rotation same-motion) was already in place.
- Affects: regenerate the derived layer of engineering-standards where materialized. No living state touched.

## [3.8.0] - 2026-08-25

- Added: `session-discipline.md` **§Reply format** (user decision 2026-08-25) — the per-reply scannable close: the four-sign **status footer** (`✅ complete — nothing new deferred` / `🔔 complete — deferred: <named items>` / `🔄 continuing` / `⏸ waiting on you`; the complete bar is high — zero actionable residue, a dangling "want me to X?" means the reply is really ⏸ or the work should have been done or filed; deferrals stamp once in the arc that files them; ⏸ outranks the complete signs while anything remains with the user; live discussion holds 🔄 until explicit closure), the **item manifest** (a reply carrying ≥2 items with one needing the user closes with one evolving `# · Item · Type · Status` table above the footer; second-person types 📖 FYI / 💬 your word / 🖐 your hands; stable numbering, terminal rows shown once; board deliveries exempt — the boards ARE the manifest, cross-cited to the board delivery form), and the **anchor line** (long replies open with one blockquote restating the ask). Ported and re-derived from the maintainer's proven conversation protocol, personal machinery stripped.
- Changed: `corpus/README.md` module line updated.
- Affects: regenerate the derived layer of session-discipline (always-loaded instructions where materialized). No living state touched.

## [3.7.0] - 2026-08-25

Compensation pass (user decision 2026-08-25): the benefits module is renamed and widened — pay joins the portfolio, and the scope gets its crisp boundary test (design principle 28).

- Renamed + widened: `benefits.md` → `compensation.md` ("Compensation — pay and the money-valued claims"). Scope test: a thing belongs iff it is money or directly priceable in money. Four kinds: **pay** (new — base salary, bonus target and outcomes, stock awards + vest schedule, sign-on terms, merit/raise mechanics; pay-affecting cycles ride the due lane; the promotion case stays in `career.md`, the pay outcome lands here, cross-pointed) · benefit elections · budgets · access. Career development still fails the test and stays in `career.md` §Growth. Register renamed `local/state/benefits.md` → `local/state/compensation.md`. Boundary split unchanged in substance: pay structure and windows live here; holdings, account values, and portfolio math stay in the user's own estate.
- Changed (reference sweep): `corpus/README.md` module line (also fixes its stale register name `resources.md`) · `UNFOLD.md` estate list + founding step 6 (pay components seed from the offer packet) · `store.md` view list · `devices.md` · `estate-structure.md` (attention view, kinds roster, data-shape examples) · `finder.md` consumers + standing watches · intake §19 (retitled compensation catalog; gains the pay-components item; programs line marked as routing to career §Growth) · `career.md` preamble cross-pointer. History surfaces (older changelog entries, the chronicle, principles 20/26) keep the old name.
- Migration for an installed estate (at the next update pull): rename the project directory `benefits/` → `compensation/` and the register `benefits.md` → `compensation.md` inside it; update the hub registry row (name + state files + edges). Register data is moved, never lost.
- Affects: regenerate the derived layer of the renamed module (and the intake checklist where materialized). Living register state is renamed in place, never rewritten.

## [3.6.0] - 2026-08-25

- Added: `human-agent-collaboration.md` **§The board delivery form** (user decision 2026-08-25) — the ONE standing format for every recurring orientation or status delivery (day-start page, sweep reports, "where are things" answers): a headline sentence, then a single page of partitioned boards. Partition law (every item on exactly ONE board; placement test top-down, first match wins: ACTION ranked · CALENDAR with prep pointers · DEADLINE with the deadlines-ahead tail line and the sanctioned cross-day move to ACTION · TEAM · PORTFOLIO · MAIN · KNOWLEDGE), uniform line anatomy (`[source] · what · when-marker · pointer`, one visible line per item, re-listed items carry age), normal-length-or-absent readability, silence rules (empty boards say nothing; no waiting board; one counts/degradation tail line), and ACTION numbering as the delivery's reference numbering. Board set adapts per install; the partition law, line anatomy, and silence rules are the form (ported and re-derived from the maintainer's proven daily-orientation board standard, personal machinery stripped).
- Changed: `portable-skills.md` day-start step 3 now delivers in the board form (cites the new section) instead of free-form priority naming; `corpus/README.md` module line updated.
- Affects: regenerate derived layers of human-agent-collaboration and the day-start skill materialization. No living state touched.

## [3.5.0] - 2026-08-25

- Added: `portable-skills.md` **event-prep** (user decision 2026-08-25) — prep for consequential meetings and committed work events, two grades over the one entered-prepared-left-recorded convention (`messages.md` §Meetings). Meeting grade: purpose + attendee lines from the people cards, desired outcome first with the user's asks (recipient-attention rule), expected questions with prepared answers, exit capture pre-named so the post-meeting record is a fill-in. Event grade: the four-section brief — what it is / ONE time-ordered attending table with the gated-placeholder wake rule (a placeholder field only with a dated mailbox-check watch; an event-day placeholder is a defect) / targets ranked from a real roster, opening with the aim / strategies with ask scripts and the after-event close. Both grades: the system does the doable prep itself, facts carry source + checked-date, execute-ready to the final target (ported and re-derived from the maintainer's proven event-brief standard, personal machinery stripped). Plus the cross-pointer in `messages.md` §Meetings prep bullet.
- Added: `human-agent-collaboration.md` §Standardized choice surfaces — workflow first on complex actionable matters: when a new multi-step actionable matter enters discussion with the human, the ordered workflow (time or logic order, each step's executor marked) is laid out and offered for review before actions are driven; scope deliberately excludes simple asks, work under a reviewed plan, standing procedures, and system-internal execution; piecemeal action-feeding named a failure mode (ported from a maintainer working rule settled 2026-08-25).
- Affects: materialize one new hub skill (event-prep) in the skills layer; regenerate derived layers of messages and human-agent-collaboration. No living state touched.

## [3.4.1] - 2026-08-25

Rename: the repo itself takes its current name, `work_estate` (user decision 2026-08-25) — the name now uses the corpus's own vocabulary (the work estate, per `estate-structure.md`), plainly self-describing.

- Changed: `text_docs/design.md` title and `UNFOLD.md` provenance-header format carry the new name. Headers already written under the old name remain valid; no derived layer regenerates for this.
- Migration for an installed estate (one-time, at the next update pull): point the clone's remote at the renamed repo under the same hosting account — `git remote set-url origin git@github.com:<account>/work_estate.git`, with `<account>` taken from the clone's existing remote URL (the code host redirects the old URL meanwhile, so an un-migrated clone keeps working); optionally rename the local clone directory to match. Update the seed row's clone path/name in the hub registry if recorded.
- Affects: nothing else — no convention, module, or living state changes.

## [3.4.0] - 2026-08-24

Task-store pass (user decision 2026-08-24): the store-backed task form is promoted from a conditional footnote to the STANDARD form, ported at implementation-grade spec from the maintainer's proven cutover of this convention.

- Changed: `task-convention.md` — new §The store-backed form: store as truth with `TODO.md` a banner-marked generated view · stable never-reused ids rendered `[id: tN]` (tooling addresses only; cite-by-position stands) · append-only status ledger with automatic stamps, close emits the archive line · the verb write surface (add/close/note/edit/state/rank/wake/show/list/regen/ingest/verify; adding never reorders, rank is the deliberate batch reorder) · hand edits detected by hash and absorbed by ingest (a reordered active section = the user's ranking; deleted lines reported, never silently closed; mutating verbs refuse over an un-ingested view) · declared-marker tail sections survive regeneration · wake as a standing engine job · flip-once procedure keeping the pre-flip backup · `verify` feeding the self-audit. Markdown-truth demoted to bootstrap/degraded fallback, kept flip-ready.
- Changed: `store.md` consumers — the task lists join the register roster.
- Changed: `UNFOLD.md` Phase 3 task-head bullet — task lists found STORE-FIRST where A7 provided an engine; a degraded install keeps flip-ready markdown and flips at the first update pass that finds one.
- Deliberately shipped as SPEC, not code (named decision): the seed stays tooling-agnostic; the section is implementation-grade and the estate's sanctioned agent builds the tool against the A7 engine.
- Affects: regenerate derived layers of task-convention; an installed estate flips its existing lists per the flip procedure at the next convenient sitting (living state preserved — flip parses and loads, never rewrites content).

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
