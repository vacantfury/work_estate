# Work engine — the whole work workflow, composed

*The composition module (design principle 16): the corpus's standing disciplines compose as LANES of ONE running system (the craft/standards modules — role-playbook, engineering-standards, agent-reliability, human-agent-collaboration, portable-skills — underpin the lanes rather than being lanes themselves); this module holds only the composition and the agent-jobs layer that keeps the lanes running. It cites the lane modules and never copies their content — each lane's procedure stays canonical in its own module.*

*Estate form (design principle 19): the engine is the HUB's organ — the registry, queue, and budget live in the hub — while each lane's state lives in its OWN estate project. `local/state/<file>` paths below resolve to the owning project's state home via the hub's estate registry.*

## The operating claim

The engine exists to invert the effort ratio: **the user devotes as little attention as possible; the system devotes as much as the available budget allows.** User attention is the scarcest resource in the whole workflow; agent tokens are the cheapest. Anything an agent can carry, an agent carries. The user's residue is typed with the vocabulary of `human-agent-collaboration.md` — they participate only as:

- **authority gate** — decisions, sends, and anything person-facing or irreversible;
- **taste judge** — quality calls the system cannot calibrate alone;
- **ground-truth source / eyes** — what only they observe (meetings, hallway signal, their own state);
- **hands** — the physical and the auth-walled.

Everything else is the system's work, run either inside working sessions or as standing agent jobs.

## Where it runs

Everything in this module runs **on the work machine, under the work account, inside the employer-sanctioned tooling and its token/compute budget** (intake §17; unfold A1). None of the user's own accounts, credentials, endpoints, or token budgets are ever part of the engine — it runs on work surfaces only (boundary discipline, `boundary-protocol.md`).

**Calibration (settled 2026-08-15):** the work-surfaces rule targets the user's own ESTATE — their repos, credentials, agent systems, token budgets. The user's incidental presence on the work machine (browser logins such as a personal mail account, a personal browser profile, ordinary browsing) is normal life and is accepted, never engineered around. Agent jobs still default to WORK surfaces only; anything a lane wants from beyond the job arrives through the user's own word, never by an agent reaching into their logins.

## The lane roster

| Lane | Canonical module | Standing state (`local/state/`) | Standing work |
|---|---|---|---|
| Delivery — accepted projects | `project-lifecycle.md` + `dev-workflow.md` | `projects.md`, `projects/<name>.md` | dev funnel execution, board upkeep, stage-event artifacts |
| Research | `research-workflow.md` + `auto_research.md` | per-project records | grounding, experiment loop, auto-research jobs + candidate funnel |
| Project sourcing | `project-lifecycle.md` (stage 1) | `projects.md` candidates | continuous candidate scan + per-candidate intelligence |
| Company intelligence | `company-watch.md` | `company.md` | signal capture, register upkeep, planning-rhythm distillation |
| Connections | `people.md` | `people.md` | register upkeep, relationship analysis, proposed moves |
| Communication craft | `communication-craft.md` | `communication.md` | artifact harvest + coaching, pre-send assists |
| Risk register | `risk-register.md` | `risks.md` | premortems at accept/transitions, reaction-plan upkeep, calibration |
| Health guard | `health-guard.md` | `health.md` | floor enforcement, tracker upkeep, breach surfacing |
| Record & accounting | `work-record.md` + `work-report.md` | `worklog.md`, `timelog.md`, `worklog-public.md` | daily capture, public-view render, Tue/Thu report build |
| Boundary | `boundary-protocol.md` | — | record-grain enforcement, content-placement rules |
| Sidework | `sidework.md` | `~/sidework/` | grab on ask, jot upkeep |
| Substrate | `task-convention.md` + `session-discipline.md` | `TODO.md`, `NOW.md`, `archive.md` | every session, every lane |

## The running loop

Three execution surfaces, by who moves:

1. **Working sessions** (the user is present, directing work): execute the delivery/research work of the day AND carry the session-time lane duties their modules already define — worklog append at close, board updates at state change, health floors named at the moment, capture-at-settle.
2. **Standing agent jobs** (the system moves alone, within budget): the scheduled/background runs in the registry below — each maintains its lane's state without the user, surfacing only what its escalation rule says earns their attention. Nothing-due runs stay silent.
3. **User moments** (deliberately few, all named): the one-minute day-end worklog pass · the Tue/Thu report hand-off · carrying boundary messages · meetings and human contact · gate decisions the jobs escalate. This list is the user's WHOLE standing cost; growing it needs a named reason.

## The agent-jobs registry — `local/state/agent-jobs.yaml`

The registry is the engine's config (parameters live in config, `engineering-standards.md`): one entry per standing job, seeded by the unfold, tuned in place. Schema per job:

- `id` · `lane` (roster row) · `purpose` (one line)
- `cadence` — how often it wants to run (daily / per-session / weekly / on-event)
- `priority` — position in the budget-ranked queue (see below)
- `output` — the `local/state/` home it writes (a job with no output home is a defect)
- `escalation` — the ONE rule for what reaches the user (default: nothing; findings land in the output home and the session-start surfaces)
- `gate` — any step that is prepare-only (person-facing contact, outbound sends, anything irreversible: the job stages, the user presses — always)
- `stage` (optional; the autonomy gradient below) — present only once a job is trusted past review-everything, together with the one-line evidence that earned the promotion
- `marker` + `silence_h` (scheduled jobs only; the autonomy gradient below) — the job's success marker and its maximum tolerated silence

**Budget-ranked queue:** jobs run in priority order until the period's budget is spent — whatever the work account's real budget turns out to be, it burns top-down, so a small budget runs the head of the queue well and a large budget runs the tail too. The budget figure, the sanctioned runtime, and whether unattended/scheduled runs are permitted at all are intake facts (§17), never assumptions. **Tuning path:** priorities and cadences are reviewed against evidence at the Tue/Thu retro (`work-report.md`) — each job's output value vs its spend; a job nobody's lane consumed for two review cycles is demoted or cut.

**The platform that executes this registry is `autoflow.md`** (mechanics/meaning split): the registry here is the engine's MEANING — which jobs exist, lanes, escalation, gates; scheduling, cycle runtime, worker dispatch, the run ledger, liveness mechanics, and runtime adaptation are the platform's and are canonical there.

**Ample-budget posture (the expected case, settled 2026-08-24):** where the discovered budget is ample, scarcity machinery stays dormant — the FULL job roster runs on cadence, priorities order execution rather than ration it, and spare capacity is spent on DEPTH before speed: stronger verification forms (the reliability module's ladder), wider digs, more frequent scoring runs, richer triage. The budget-ranked queue above is the fallback for genuinely constrained environments, never the default posture.

## The autonomy gradient (direction; hardens only at its named triggers)

A standing job's trust is graded on three INDEPENDENT axes. There is deliberately no single fused "level": one number cannot carry three different questions, and fusing them loses exactly the grain that keeps autonomy safe (a mature job can still contain irreversible steps; a young job can be safe to run when all its steps are mechanical).

1. **Action seriousness decides the CHECKING each output gets.** This axis is already binding from birth: the irreversibility classes and verification ladder of `agent-reliability.md`, and the registry's `gate` field. Nothing here is soft.
2. **Capability maturity decides the AUDITING cadence:** how much of a job's output the user still reviews. Three stages: every output reviewed → exceptions reviewed (the job filters, the user sees what it flags) → sampled audits (the job runs, the user audits a periodic sample). A promotion is EARNED by named evidence (a run record at the current stage in which the user had no corrections to make), recorded in the entry's `stage` field at promotion. Demotion is free and immediate: any correction the user has to make drops the job back one stage, no ceremony.
3. **Runtime liveness decides the MONITORING**, for jobs that run unattended. Silent death is the failure class: a scheduled job that stops running looks exactly like a quiet one unless something checks. The cure is declared, not assumed: the entry's `marker` + `silence_h`, checked at every session opening (silence past the window is a surfaced finding, never presumed fine). If the runtime ever gains deploy structure (a pinned what-runs version, external consumers of its paths or names), those facts register in the entry the day they exist, and any rename or path change consults the registered consumers before it lands.

**Named triggers.** Until each fires, this section is direction only and costs nothing:

- *Trigger 1* — the first sanctioned scheduled/unattended job: its entry carries `marker` + `silence_h` from creation, and the session-opening sweep starts checking markers.
- *Trigger 2* — the first job trusted past review-everything: its entry gains `stage` plus the evidence line.

**Permanent boundaries, at every stage:**

- Real product development is not governed by this gradient. The team's own pipeline (design rituals, CI, staging, release trains, monitoring) IS the structure for delivered work (`dev-workflow.md`, team reality first). The gradient governs only the estate's own standing jobs.
- Maturity buys back the user's REVIEW attention, never authority. Person-facing, employer-visible, and irreversible steps stay prepare-only at every stage (rails 2 and 5; `agent-reliability.md` irreversibility). No stage, cadence, or clock ever converts a gate into an auto-run.

## Rails (binding on every job)

1. **Work account, sanctioned tooling, work surfaces only** — a job never touches a personal login, endpoint, or credential, even one present on the machine.
2. **Prepare-only at the human edge:** no job sends, posts, submits, or contacts a person autonomously — it stages, the user presses.
3. **Team norms bind:** jobs conform to the team's real AI-use norms and output-pace tolerance (design principle 10); agent output on team-visible surfaces is written for its human readers.
4. **Records candid, one home:** job outputs follow the standing record posture (candid and complete, `work-record.md`) and the one-home rule — jobs write their lane's state file, never a parallel copy.
5. **Health floors outrank the engine:** no job or queue pressure ever argues against a floor (`health-guard.md`).
