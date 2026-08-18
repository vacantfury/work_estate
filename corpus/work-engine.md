# Work engine — the whole work workflow, composed

*The composition module (design principle 16): the corpus's standing disciplines compose as LANES of ONE running system (the craft/standards modules — role-playbook, engineering-standards, agent-reliability, human-agent-collaboration, portable-skills — underpin the lanes rather than being lanes themselves); this module holds only the composition and the agent-jobs layer that keeps the lanes running. It cites the lane modules and never copies their content — each lane's procedure stays canonical in its own module.*

## The operating claim

The engine exists to invert the effort ratio: **the owner devotes as little attention as possible; the system devotes as much as the available budget allows.** Owner attention is the scarcest resource in the whole workflow; agent tokens are the cheapest. Anything an agent can carry, an agent carries. The owner's residue is typed with the vocabulary of `human-agent-collaboration.md` — he participates only as:

- **authority gate** — decisions, sends, and anything person-facing or irreversible;
- **taste judge** — quality calls the system cannot calibrate alone;
- **ground-truth source / eyes** — what only he observes (meetings, hallway signal, his own state);
- **hands** — the physical and the auth-walled.

Everything else is the system's work, run either inside working sessions or as standing agent jobs.

## Where it runs

Everything in this module runs **on the work machine, under the work account, inside the employer-sanctioned tooling and its token/compute budget** (intake §17; unfold A1). None of the owner's own accounts, credentials, endpoints, or token budgets are ever part of the engine — it runs on work surfaces only (boundary discipline, `boundary-protocol.md`).

**Calibration (owner ruling, 2026-08-15):** the work-surfaces rule targets the owner's own ESTATE — his repos, credentials, agent systems, token budgets. His incidental presence on the work machine (browser logins such as Gmail, an Edge profile, ordinary browsing) is his normal life and is accepted, never engineered around. Agent jobs still default to WORK surfaces only; anything a lane wants from beyond the job arrives through the owner's own word, never by an agent reaching into his logins.

## The lane roster

| Lane | Canonical module | Standing state (`local/state/`) | Standing work |
|---|---|---|---|
| Delivery — accepted projects | `project-lifecycle.md` + `dev-workflow.md` | `projects.md`, `projects/<name>.md` | dev funnel execution, board upkeep, stage-event artifacts |
| Research | `research-workflow.md` | per-project records | grounding, experiment loop, auto-research jobs |
| Project sourcing | `project-lifecycle.md` (stage 1) | `projects.md` candidates | continuous candidate scan + per-candidate intelligence |
| Company intelligence | `company-watch.md` | `company.md` | signal capture, register upkeep, planning-rhythm distillation |
| Connections | `connections.md` | `people.md` | register upkeep, relationship analysis, proposed moves |
| Communication craft | `communication-craft.md` | `communication.md` | artifact harvest + coaching, pre-send assists |
| Risk register | `risk-register.md` | `risks.md` | premortems at accept/transitions, reaction-plan upkeep, calibration |
| Health guard | `health-guard.md` | `health.md` | floor enforcement, tracker upkeep, breach surfacing |
| Record & accounting | `work-record.md` + `work-report.md` | `worklog.md`, `timelog.md`, `worklog-public.md` | daily capture, public-view render, Tue/Thu report build |
| Boundary | `boundary-protocol.md` | — | record-grain enforcement, content-placement rules |
| Sidework | `sidework.md` | `~/sidework/` | grab on ask, jot upkeep |
| Substrate | `task-convention.md` + `session-discipline.md` | `TODO.md`, `NOW.md`, `archive.md` | every session, every lane |

## The running loop

Three execution surfaces, by who moves:

1. **Working sessions** (the owner is present, directing work): execute the delivery/research work of the day AND carry the session-time lane duties their modules already define — worklog append at close, board updates at state change, health floors named at the moment, capture-at-settle.
2. **Standing agent jobs** (the system moves alone, within budget): the scheduled/background runs in the registry below — each maintains its lane's state without the owner, surfacing only what its escalation rule says earns his attention. Nothing-due runs stay silent.
3. **Owner moments** (deliberately few, all named): the one-minute day-end worklog pass · the Tue/Thu report hand-off · carrying boundary messages · meetings and human contact · gate decisions the jobs escalate. This list is the owner's WHOLE standing cost; growing it needs a named reason.

## The agent-jobs registry — `local/state/agent-jobs.yaml`

The registry is the engine's config (parameters live in config, `engineering-standards.md`): one entry per standing job, seeded by the unfold, tuned in place. Schema per job:

- `id` · `lane` (roster row) · `purpose` (one line)
- `cadence` — how often it wants to run (daily / per-session / weekly / on-event)
- `priority` — position in the budget-ranked queue (see below)
- `output` — the `local/state/` home it writes (a job with no output home is a defect)
- `escalation` — the ONE rule for what reaches the owner (default: nothing; findings land in the output home and the session-start surfaces)
- `gate` — any step that is prepare-only (person-facing contact, outbound sends, anything irreversible: the job stages, the owner presses — always)

**Budget-ranked queue:** jobs run in priority order until the period's budget is spent — whatever the work account's real budget turns out to be, it burns top-down, so a small budget runs the head of the queue well and a large budget runs the tail too. The budget figure, the sanctioned runtime, and whether unattended/scheduled runs are permitted at all are intake facts (§17), never assumptions. **Tuning path:** priorities and cadences are reviewed against evidence at the Tue/Thu retro (`work-report.md`) — each job's output value vs its spend; a job nobody's lane consumed for two review cycles is demoted or cut.

**Runtime adaptation (resolved by the unfold, A1):**
- *Full agent harness with scheduled runs sanctioned* → jobs run as actual scheduled/background agents.
- *Assistant-only tooling, or unattended runs not sanctioned* → the registry becomes the **session-opening sweep**: each working session starts by running the due jobs' procedures inline, highest priority first, time-boxed.
- *No sanctioned tooling (degraded path)* → the lanes survive as session disciplines and printed checklists; the registry documents intent for a later re-run.

## Rails (binding on every job)

1. **Work account, sanctioned tooling, work surfaces only** — a job never touches a personal login, endpoint, or credential, even one present on the machine.
2. **Prepare-only at the human edge:** no job sends, posts, submits, or contacts a person autonomously — it stages, the owner presses.
3. **Team norms bind:** jobs conform to the team's real AI-use norms and output-pace tolerance (design principle 10); agent output on team-visible surfaces is written for its human readers.
4. **Records candid, one home:** job outputs follow the standing record posture (candid and complete, `work-record.md`) and the one-home rule — jobs write their lane's state file, never a parallel copy.
5. **Health floors outrank the engine:** no job or queue pressure ever argues against a floor (`health-guard.md`).
