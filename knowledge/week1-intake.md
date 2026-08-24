# Week-1 intake checklist — the axis-2 assumptions ledger

*Every entry below is an assumption or open question produced by the pre-start research (`role-workflow-research.md`) — the operational half of axis 2 (`text_docs/design.md`, four-axis build model). At intake (axis 3), each entry gets confirmed, refuted, or refined against the actual team environment. **Answers are work-derived: they are recorded in `local/` (the unfold's ledger or `local/state/` notes), never in this committed file.** The unfold's detect phase walks this checklist; entries also serve as a plain human week-1 question list on the degraded path.*

*Legend: ☐ = to resolve at intake · **[assume: …]** = working assumption to verify, with the research section it came from.*

## 1. Sanctioned AI tooling (feeds unfold A1)

- ☐ Which AI coding assistant(s) are sanctioned on the corp device, and which surfaces (IDE chat, CLI, autonomous agent)? **[assume: GitHub Copilot family, not Claude Code — third-party press reports an internal Claude Code revocation with a mid-2026 cutover to GitHub Copilot CLI; unconfirmed → research §3.4]** Ask directly; don't rely on press.
- ☐ What instructions/memory format does the sanctioned assistant consume (repo instructions file, org-managed config)? Decides the unfold's generated instructions layer.
- ☐ Are external LLM endpoints reachable at all from the device, and under what policy?

## 2. Code, build, and pipeline

- ☐ Is the team's code on GitHub Enterprise or Azure Repos? **[assume: GitHub or mid-migration — the Copilot-adjacent org piloted the company's Repos→GitHub migration → research §3.4]**
- ☐ Planning and CI: Azure Boards + Azure Pipelines/1ES alongside GitHub, or GitHub-native? Locate the 1ES/build onboarding doc for the team's repos.

## 3. Data and telemetry (the biggest unlock)

- ☐ Where do eval sets and production telemetry actually live (Fabric workspace, Kusto/ADX, Cosmos/SCOPE, AML workspace)? **Not publicly documented — must ask. → research §3.3**
- ☐ What is the day-to-day query tooling (KQL, SCOPE, Spark/SQL)?
- ☐ Is there a team "data platform 101" onboarding doc? Locate it; if none exists, notes taken while learning it are a candidate first contribution (kept in `local/`).
- ☐ What access reviews/approvals gate the team's datasets, and what Purview classification do they carry?
- ☐ What is the actual internal "eyes-off"/restricted-access process for eval and telemetry data? **Not public — must ask before touching any dataset. → research §3.6**
- ☐ Do EU Data Boundary constraints touch the team's data or model choices (note the published carve-out: Anthropic models excluded from EUDB commitments)? → research §3.6

## 4. Experimentation

- ☐ Does the team flight through ExP directly or an org-specific layer on top? → research §3.1
- ☐ How are LLM response-quality metrics (vs classic engagement metrics) wired into experiment analysis? **Open question — the public ExP corpus predates the LLM era.**
- ☐ What is the standard ramp (rings, dogfood cohorts, enrollment percentages) for a model/prompt change?
- ☐ What are the team's standing guardrail metrics, and where do experiment readouts live?

## 5. Eval practice (calibrates the role-playbook corpus module)

- ☐ What eval harness/suites already exist? Is there a capability-vs-regression split, or an equivalent convention? → research §2.3
- ☐ How are LLM-judges built and calibrated today — against what human-label process?
- ☐ How do scientists access and read production transcripts (privacy-compliant), and what annotation tooling exists?
- ☐ Is there an established error-analysis/failure-taxonomy practice, or is that a gap the playbook's conventions could fill (team standard wins either way)?
- ☐ How does the team qualify a candidate model/provider today — which suites, what declared bar, who signs off, where do qualification readouts live? → research §2.3, playbook model-migration discipline
- ☐ Is there a provider-agnostic model seam (proxy layer) in the product, and who owns it? How are per-model prompt/scaffold variants versioned? → research §2.2

## 6. Architecture surface

- ☐ Which layer does the team actually own: retrieval/grounding, orchestrator routing/planning, model training, response generation, safety filtering? Decides which evals and telemetry matter. → research §3.2, §1.1
- ☐ Is there internal developer-mode-style telemetry exposing orchestrator decisions for debugging/evals? → research §3.2

## 7. Responsible AI

- ☐ Locate the team's most recent RAI Impact Assessment and its owner; identify the RAI point of contact. → research §3.5
- ☐ At what lifecycle point must an impact assessment start (before first flight vs before GA)? Does any team surface trigger Sensitive Uses review?

## 8. Team rhythm and role scope

- ☐ Actual planning cadence: sprint length, season/semester structure, sprint-end reporting ritual, OKR structure. **[assume: 3-week sprints within ~6-month seasons, per the company's published planning model — verify → research §1.5]**
- ☐ The team's actual charter: which of the five posting-level responsibility areas (orchestrator reasoning · model training · retrieval · eval infra · feature shipping) is the real center of gravity? → research §1.1
- ☐ Manager conversation, week 1: what does great impact look like at this level against the three Connect circles (individual · enabling others · building on others)? Level-specific expectations are not public. → research §1.4
- ☐ Where does the team keep its knowledge (wiki, docs repo, OneNote/Loop) — the home for any conventions worth proposing later.

## 9. People and expectations (calibrates the playbook's working-in-the-org section)

- ☐ Map the people who matter to this role's success: manager, skip-level, the senior scientists on the team, and the cross-team partners the charter depends on. Which of them welcome recurring 1:1s?
- ☐ What the review rhythm actually looks like on this team: Connect timing, how impact evidence is gathered through the period, what record-keeping the manager expects between Connects. (Extends the §8 manager conversation.)
- ☐ Where delivered work gets seen — demo slots, sprint readouts, team channels — and which of those channels leadership actually reads.

## 10. Time, presence, and pace (feeds design principle 9)

*Both sources are mandatory here: the written policy AND what teammates say they actually do — the real norm is discovered, never assumed from the policy text.*

- ☐ The official hybrid/in-office policy as written: minimum days per week, whether specific days are designated, any presence tracking (badge data), and the exception/accommodation process. **[assume: a written minimum-cadence policy exists; the team's real norm may sit anywhere relative to it — verify]**
- ☐ The team's REAL presence practice, asked of teammates directly: which days people actually come in, typical arrival/departure times, which days the manager and key partners attend, and how remote days are regarded on this team.
- ☐ Real working-hours norms: core/overlap hours, after-hours and weekend responsiveness expectations (chat/email), and any predictable crunch periods around releases.
- ☐ Manager's actual expectation on presence and availability, in their own words (fold into the §8 week-1 conversation).
- ☐ Calibration output (recorded in `local/`, per design principle 9): the chosen presence/hours baseline — the level within the team's real norm that fully serves delivery and the §9 relationship map — and the recurring on-site anchors (1:1s, demos, team rituals) the attended days are built around.

## 11. Team conventions as practiced (feeds design principle 10)

*Triple-source mandate, extending §10's dual-source rule: official docs AND the artifacts (code, merged PRs, review threads) AND teammates directly. A long-history team's real conventions may be non-standard, non-optimal, and documented nowhere — the divergence between the written guide and actual practice IS the convention.*

- ☐ Before writing any code: read the team's main repos and the last ~20–30 merged PRs — naming/style/structure as actually practiced, PR size norms, commit-message style, test expectations as enforced in review (vs as documented).
- ☐ Review culture: expected turnaround, who must approve what, nit level, how disagreement is handled in review, whether design docs or pre-review pairing are expected before a PR.
- ☐ Process as practiced vs as documented: the branch/CI/release ritual people actually follow, and the undocumented tribal steps — ask directly: "what's the real way to do X that no doc says?"
- ☐ Who carries the history: the long-tenured people who know why conventions are what they are; ask for the why before ever proposing a change, and learn which past change proposals died and why.
- ☐ The team's channel for convention change (where proposals are made, who decides) — the path to use later, once standing is earned; never unilateral deviation meanwhile.
- ☐ AI-use norms in practice: how teammates actually use the sanctioned assistant day to day, disclosure expectations for AI-assisted work, how AI-generated code is received in review, and what volume of agent-produced output the human review loop comfortably absorbs.

## 12. Project landscape and staffing reality (feeds design principle 11)

*The project pipeline (`corpus/project-lifecycle.md`) needs the team's real staffing mechanics before it can run — same triple-source rule: docs AND artifacts AND asking people directly.*

- ☐ How projects actually get born and staffed on this team: assigned top-down, volunteered, negotiated in planning — and in which ceremony (sprint planning, season planning, ad hoc)? Who actually staffs — the manager alone, leads, PM?
- ☐ The current project menu: what's live, what's upcoming or unstaffed, what's wished-for but unowned. This is the seed content for the portfolio board (`local/state/projects.md`).
- ☐ What the org visibly values: what recent promotions at this level were built on, which projects leadership names unprompted, what sits on the charter's critical path. (Extends §9's where-work-gets-seen.)
- ☐ The team's channel and norms for self-proposed work: is there a PoC/prototype culture, a doc-first proposal ritual, hack time — how does an initiative project legitimately get born here, and who says yes?
- ☐ Per-project visibility expectations: what cadence of visible progress the team expects on an active project, and where landings get presented and credited.
- ☐ How refusal and capacity trade-offs are actually voiced here: watch how teammates decline or renegotiate work before using the prioritization framing — the team's real idiom wins over the module's default phrasing.

## 13. Company baseline: leadership, people, and direction surfaces (feeds design principle 12)

*Seeds the company watch (`corpus/company-watch.md`): the source map, the leadership chain, and the initial registers — recorded in `local/state/company.md`, never here. Scope is the whole company — the own org watched most closely, proximity weighting attention but never drawing the boundary; the record candid and complete, for the user's benefit.*

- ☐ Map the leadership chain by name: manager → skip → org lead → division/company leadership; for each, what they formally lead and what they visibly push. Add the notable leaders OUTSIDE the chain worth tracking from day one — company leadership and adjacent-org owners of themes that touch the team's path. (The leader register's first fill.)
- ☐ Map the surfaces at each level: all-hands and town halls (company, org, team), leadership memos and newsletters, cross-org channels, where planning artifacts (OKRs, commitments, charters) live — and where personnel news actually lands: promotion announcements, departure notes, org-chart changes, in the own org and company-wide. (Extends §9's where-leadership-reads with where-leadership-writes.)
- ☐ The recent record, asked of teammates: the last promotion round — who, and what it was built on; recent departures and reorgs and their stated reasons. First fill of the event register and the reward map. (Extends §12's what-gets-valued with what-gets-penalized.)
- ☐ Seed the initial theme register from onboarding materials, the team charter, and the most recent all-hands at each level — graded honestly by the evidence ladder: most onboarding rhetoric enters at the lowest grade until resourcing or repetition confirms it.
- ☐ Ask the manager directly: what is leadership pushing this half; which themes are gaining or losing headcount and funding; where does the team's charter sit on the org's critical path. (Extends §12's what-gets-valued.)
- ☐ Identify who owns each rising theme and who is visibly rising — the people to pre-position relationships with early (feeds the §9 relationship map).

## 14. Health facilities and the wall (feeds design principle 13)

*Binding grounding rule: facility docs FIRST, then ask the user where the docs don't answer — no facility practice is assumed. The resolved facility map is recorded in `local/`, never here.*

- ☐ Locate the facilities/benefits documentation and build the facility map: ergonomics program and the equipment-request channel, sit-stand desk availability, gym/fitness access, cafeteria locations and hours, break spaces and walking routes. **[assume: a large-campus employer documents all of these; the request channels are what varies — verify]**
- ☐ Week 1, at eligibility: submit the ergonomic setup — chair fitting, monitor at eye height, external keyboard/mouse. Request equipment early; never wait for pain.
- ☐ Home-equipment provision (settled 2026-08-14 — employer-provision-first): does the employer provide or reimburse home-office equipment (monitor, keyboard/mouse, chair), through which channel and up to what allowance? Checked BEFORE any personal purchase — the home station is furnished through this channel first; personally bought only what it doesn't cover.
- ☐ Home station (WFH days), furnished after start via the channel above: same ergonomic bar — real desk, real chair, external monitor — and ONE dedicated work spot (the wall's physical mechanism).
- ☐ On-call reality: does the role carry a rotation; which channel/tooling it genuinely requires, at what response expectation, on what schedule (docs AND teammates — §10's dual-source rule). Scope the wall's carve-out to exactly that.
- ☐ Set with the user and record in the ledger: the hard-stop time, the lunch block, and the moment-table cadences (`corpus/health-guard.md`).
- ☐ Wire the guard's clock: the best reminder mechanism the device and sanctioned tooling offer (calendar blocks, OS/assistant break reminders, the agent's own surface; degraded path: phone timers + the printed moment table).
- ☐ Set the distillation cadence: which planning-rhythm checkpoint (§8) the register refresh and portfolio alignment re-score ride on.

## 15. Work-record home and status conventions (feeds design principle 14)

*The private record (`local/state/worklog.md`, `corpus/work-record.md`) is unconditional; what intake resolves is the PUBLIC VIEW's home and cadence. Same grounding as everywhere: docs and artifacts first, then ask — never assumed.*

- ☐ Does the team already have a status-record convention — weekly snippets, standup posts, sprint readout notes, a wiki/status page, per-person status threads? Read a few weeks of whatever channel exists (the artifacts) before asking anyone.
- ☐ Ask the manager directly (fold into the §8/§9 week-1 conversation): where would they want to see a running record of delivered work, and at what cadence? This is the mechanism behind §9's record-keeping-between-reviews question.
- ☐ Ask a teammate: where does status actually get posted AND read here — which of the existing surfaces does the manager (or leads) really look at?
- ☐ Resolve and record in `local/`: the public view's home (an existing team surface, a new page in the team's knowledge home (§8), or the manager's 1:1 doc) + the render cadence (ride an existing ceremony where one exists; weekly default). Until resolved, the rendering stages at `local/state/worklog-public.md`.
- ☐ Confirm the private capture rhythm with the user: session-end appends + their one-minute end-of-day pass.

## 16. Environments, promotion, and design ritual (feeds design principle 15)

*The dev workflow's environment ladder and stage gates (`corpus/dev-workflow.md`) bind to the team's REAL infrastructure and process — discovered, never assumed; same triple-source rule (docs AND artifacts AND teammates).*

- ☐ The real environment ladder: what exists between a dev machine and production (shared test/staging, dogfood, canary rings, experiment flights) and what each rung is actually used for.
- ☐ The promotion ritual per rung: what gates a deploy to each environment (approvals, checks, sign-offs), who owns it, how rollback actually works, and how long a ramp typically runs. (Extends §4's ramp question from experiments to all deploys.)
- ☐ Monitoring per environment: what telemetry/dashboards exist and where, what the team actually watches after a deploy, and what counts as a regression worth halting a ramp.
- ☐ The design ritual: are designs written and reviewed before build (design doc, ADR, spec review) — in what form, by whom, above what project size? Where do design decisions get recorded, and does that surface double as the project record's home?
- ☐ The spike/prototype norm: are time-boxed pre-experiments a recognized work form here (spike stories, prototype branches, hack time)? How are their results reported and credited?
- ☐ Variant practice: is building and flighting multiple candidate variants normal on this team (ties to §4 experimentation), and what does a respected comparison look like — or is single-variant-plus-iteration the culture?

## 17. Agent runtime and token budget for the work engine (feeds design principle 16)

*The work engine's agent-jobs layer (`corpus/work-engine.md`) runs entirely on the work account inside sanctioned tooling — its whole shape depends on three facts discovered here, never assumed. Extends §1 (which tooling exists) with what that tooling may DO.*

- ☐ What token/compute budget does the work account actually have (assistant seat quotas, internal model endpoints, request caps, org GPU/inference allowances), and is it per-person, per-team, or effectively uncapped for ordinary use?
- ☐ May agents run scheduled or unattended on the device (background tasks, cron-like runs, long-running agent sessions), or is agent use interactive-only by policy or by tooling shape? Decides queue mode: scheduled agents vs the session-opening sweep (`work-engine.md`).
- ☐ What can the sanctioned agent actually reach (repos, internal docs/wikis, experiment systems, dashboards, mail/calendar via work Graph APIs)? Each reachable surface unlocks lanes (auto-research scouts, register upkeep, experiment monitor); each unreachable one degrades a lane to session-time upkeep.
- ☐ The team's tolerance for standing agent work in practice (principle 10): is background agent usage of shared resources ordinary, noticed, or frowned on? Calibrates cadences and priorities in the registry.
- ☐ Where should the job registry's budget knob be set initially — a conservative share of the discovered budget, raised as the Tue/Thu retro shows value? Record the starting figure and its basis in `local/ledger.md`.

## 18. Personal-stack feasibility: research from the work machine (feeds design principle 17)

*The graded boundary allows the personal research stack on the work device (`corpus/research-infrastructure.md`); whether each leg actually works under policy is discovered, never assumed. A peer's answer on real-world practice is pending at seed time — fold it in when it arrives; the work docs decide wherever they speak.*

- ☐ Personal git hosting from the device: reachable at all? Read-only or push too (network proxy/DLP, git credential policy)? Verify the push leg with a trivial test commit to a private test repo before relying on it.
  - 2026-08-18 finding: the device's enterprise-managed GitHub account cannot accept collaboration invitations to repos outside the enterprise (invitation refused). Invitations are therefore never the access route — an outside PRIVATE repo reaches the device only via the per-device credential (`corpus/research-infrastructure.md` item 2); PUBLIC repos clone credential-free (this seed's own channel). github.com reachable in the browser (the invitation attempt rendered); the git clone/push legs remain unverified.
- ☐ Policy on ACTIVE personal projects on the device (sharpens A3/Phase 0, which asked only about this conventions seed): personal repos worked on, personal tools installed, personal secret-manager sign-in — allowed, tolerated, or prohibited?
- ☐ External/personal LLM endpoints from the device: permitted at all, and for which content classes? This answer decides every gray flow in the two-stack rule.
- ☐ May work-confidential content run on non-employer compute (the user's own clusters), or is work content bound to employer devices/tenancy? Default before the answer: no.
- ☐ The employer secret store and LLM gateway the team actually uses — the work stack's incumbents (extends §1 and §17).
- ☐ Record every answer plus the chosen sync posture (full client vs read-only satellite) in `local/ledger.md`; on a blocked-push outcome, name the fallback explicitly.

## 19. Resource catalog: benefits, budgets, programs, access (feeds design principle 20a, `corpus/benefits.md`)

*The catalog is discovered, never assumed — the failure mode is the resource nobody mentions. Portal-first, then ask HR/the manager/a tenured teammate what people actually use and forget to use.*

- ☐ **The new-hire enrollment window, FIRST:** when it opens, when it closes, and what falls into it (health insurance, retirement elections, stock purchase enrollment, HSA/FSA-class accounts). Read it off the enrollment portal the day the portal opens; land every close date as a buffered `[due:]` line. **[assume: the window is short (weeks) and closing it is irreversible until the next annual cycle — verify]**
- ☐ Retirement mechanics as offered: employer match formula and vesting, contribution limits, any after-tax contribution + in-plan conversion path, default investment vs available lineup.
- ☐ Stock programs: purchase-plan terms (discount, periods, enrollment windows) and any grant/vesting mechanics relevant to elections.
- ☐ The full benefits/perks catalog beyond the big four: wellness allowances, commuter, insurance riders, legal/backup-care/assistance programs — one register line each, even if declined.
- ☐ Claimable budgets: learning/training, conference, equipment/home-office — amounts, cycle reset dates, claim mechanics, what actually gets approved in practice.
- ☐ Programs: patent/invention awards, internal mobility rules, mentorship programs, hackathons, internal speaking/teaching venues — eligibility and application windows.
- ☐ Access worth claiming at eligibility: compute quotas, license seats, data/tool access the role can request for free.
- ☐ Cycle boundaries: when open enrollment recurs, when budgets reset — so catalog-discovery re-runs land on the calendar.

## 20. Review instrument and leveling (feeds design principle 20a, `corpus/career.md`)

*Both artifacts shape themselves to what is discovered here. The rubric as practiced wins over the rubric as written (design principle 10).*

- ☐ The review instrument itself: its name, its form (self-write vs manager-write vs both), its sections/prompts, cadence (annual, semi-annual, check-ins), and where past examples live.
- ☐ The calibration process as practiced: who is in the room, what evidence actually moves outcomes, what a strong submission looks like on this team (ask the manager for one).
- ☐ The leveling guide for the current and next level: the written bar's dimensions, and where the guide lives.
- ☐ How promotions actually happen here: recent promotions on the team/org and what visibly earned them (feeds the company watch's events register and the promotion dossier's evidence weighting).
- ☐ The manager's own view of the next-level bar and the current gaps, in their words (fold into the §8/§9 week-1 conversations).
- ☐ Timing: when the next review cycle opens, so cycle preparation lands early, never at the deadline.

## 21. Content placement: the team's real storage surfaces (feeds the placement map, `corpus/estate-structure.md`)

*The placement map is discovered, never assumed — the team's actual practice and the policy's sanctioned storage win over any default.*

- ☐ The canonical home of team docs: which system (wiki, doc suite, shared drive) the team treats as the system of record, and which of the several that exist is truth when two hold copies.
- ☐ Where meeting notes, decision records, and design docs canonically live — and whether the team distinguishes personal working notes from team-visible ones (and where each goes).
- ☐ What storage the device/data policy sanctions for work-adjacent personal notes (cross-check with A4/A6: the estate root and its backup inherit from this answer).
- ☐ Any hygiene convention for scratch space and downloads; if none, the estate names one scratch spot and a cleanup cadence.
