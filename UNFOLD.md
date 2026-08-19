# UNFOLD — the installer

*Run on the work device, in the first session after cloning. Executable by any sanctioned capable agent — or manually by the user (degraded path at the end). This file is deliberately plain markdown with no dependency on any harness, language runtime, or feature: which AI tooling may execute it is itself a question it answers (A1).*

## Contract

- **Input:** this repo (read-only during the unfold), the work documents the user points at (AI-tooling policy, device/acceptable-use policy, engineering handbook if offered), and the device itself.
- **Output:** the unfold FOUNDS the work-side ESTATE — many projects, one per design-principle-19 roster row, at the root A4 chooses — plus the ledger and log in this clone's gitignored `local/`. The committed seed is never edited by the unfold, and nothing derived from employer docs, systems, or code is ever committed or pushed — the one-way flow rule (CLAUDE.md) is absolute.
- **Re-runnable:** generated instruction/skill layers are wiped and regenerated on each run; living project state (task files, boards, registers, records) is never touched by a re-run.

## What the unfold creates

- **The estate** (at the A4 root): one directory per project — hub · people · company intelligence · records · health · communication · risk, plus per-work-project homes created later at accept (principle 19). Each project gets its instruction layer, its `TODO.md` + `NOW.md` + `archive.md` per `corpus/task-convention.md`, and its state files seeded from its genome module. Project homes are local git repos where device practice allows. The hub carries the estate registry — every project, its home, its state files; corpus references to `local/state/<file>` resolve to the owning project's state home via this registry.
- **In this clone's `local/` (gitignored):** `local/ledger.md` — the resolved A1–A6 answers, each with its deciding evidence, dated; re-runs append a new dated section, keeping history — and the unfold log.

## Phase 0 — precondition gate

1. Confirm the device policy permits a personal-convention repo on this machine (this is A3, resolved first because everything else depends on it). Evidence: the device/acceptable-use policy, or an explicit answer from the user after they check.
2. If the answer is no or remains unclear → **STOP**: delete the clone, record nothing on the device. The corpus still serves in reading form elsewhere.

## Phase 1 — detect

Gather evidence; note everything observed (it feeds Phase 2).

1. **Work docs:** read the documents the user supplies — AI-tooling policy (what agents/endpoints/tools are sanctioned), device policy, engineering standards if offered. Extract only what the ledger needs; quote policy minimally.
2. **Device inspection (read-only):** what AI/agent tooling is installed or available (internal tooling, editor agents, CLIs); what runtimes exist (`git`, `python`, `uv` versions); what backup/sync mechanisms the employer provides (managed folder sync, work-hosted git, device backup — feeds A6); whether the seed's remote is reachable (a credential-free read-only check, e.g. `git ls-remote` on this repo's public URL — the repo is public so this check needs no credential; the user's own credentials land on the device only later, per the amended credential rule in `corpus/boundary-protocol.md` and the setup order in `corpus/research-infrastructure.md`, never to make this check pass).
3. **Work stack and real conventions:** which languages/build systems dominate the repos actually worked on, and the conventions actually practiced in them — read the code and recent merged PRs, not only any written guide; the real house style may be documented nowhere (design principle 10). On the first run this may be unknown — mark it deferred; it refines A5 on a later re-run.
4. **Axis-2 assumptions:** walk `knowledge/week1-intake.md` (the pre-start assumptions ledger). Record confirm/refute/refine per entry in `local/` — some entries resolve from the same docs/inspection as steps 1–2; the rest become the user's week-1 questions. Results feed A5 and calibrate the provisional `corpus/role-playbook.md` module.

## Phase 2 — resolve the ledger

Answer A1–A6 in `local/ledger.md`, each with the one evidence line that decides it. An unanswerable question is recorded as **unresolved** with what's missing — never guessed.

- **A1 — sanctioned AI tooling.** Decides what executes future sessions and the format of the generated instructions layer — and, with the intake §17 answers (token budget, unattended-run policy, reachable surfaces), the work engine's queue mode and budget knob (`corpus/work-engine.md`). Outcome classes: a full agent harness · an instructions-consuming assistant · none (→ degraded path).
- **A2 — remote reachability.** Decides the update channel: reachable → `git pull` + re-run unfold picks up seed improvements; not reachable → the seed is refreshed rarely, by whatever sanctioned transfer route exists, or not at all.
- **A3 — personal-repo policy.** Already gated Phase 0; record the evidence here.
- **A4 — the estate root and project-home form.** Where the work-side estate lives (a work-projects directory in the user's device home, or a work-managed location if policy or practice prefers it) and what form project homes take (plain dirs · local git repos · work-hosted git). Default: a projects directory with each project a local git repo. Record the chosen root in the ledger; the estate never pushes to the seed's remote.
- **A5 — applicable convention/skill subset.** Per corpus module and per portable-skills entry: **adopt / adapt / fold away**, one-line reason each. What is folded away stays in the corpus, available to later re-runs.
- **A6 — backup of the work-side estate.** The estate never pushes to the seed's remote, so it is single-copy until a route is chosen. Decide the backup process ONLY from what Phase 1 found: the work docs (what storage the policy sanctions for work-adjacent personal notes) and the tools actually available on the device (employer-managed folder sync, work-hosted git, device backup). Never a personal cloud or the personal remote — one-way flow is absolute. If A4 rooted the estate in a work-managed location, backup may already be inherited — record that as the answer. Nothing suitable found → record **unresolved** and note that the estate is consciously single-copy until re-run.

## Phase 3 — found the estate

From the resolved ledger, found the work-side estate at the A4 root (design principle 19). Founding rules: an existing project or state file is NEVER overwritten — re-runs regenerate instruction/skill layers only; each project gets its own `TODO.md` (`# TODO (ordered)`), `NOW.md`, and `archive.md` per `corpus/task-convention.md` at founding.

1. **Found the hub** — the estate's steward project:
   - **Estate registry:** the map of every project — name, home path, state files, genome modules. No unregistered projects; corpus references to `local/state/<file>` resolve to the owning project's state home via this registry.
   - **Instructions layer (tier 1):** the always-loaded instructions file in the sanctioned tooling's native format — an agent-memory file, a repo instructions file, or (no tooling) a printable conventions one-pager. Content: the adopted estate-wide law (A5 subset of the craft/standards modules), law only — no changing facts. Per-project instruction files state each project's own scope and cite the hub's law, never copy it.
   - **Task head:** the hub's `TODO.md` is the estate head — the user's ordered next actions across projects; other projects' TODOs are tails.
   - **Agent-jobs engine:** seed the registry `agent-jobs.yaml` per the schema in `corpus/work-engine.md`, priorities/cadences drafted from the corpus defaults, queue mode set from A1 + intake §17 (scheduled agents · session-opening sweep · degraded checklists). Each job writes its OWNING project's state.
   - **Footprint register:** seed per `corpus/device-return.md`; back-fill a line for anything personal already present on the machine (this clone itself needs no line while the repo is public and credential-free; the first of the user's credentials or sign-ins does).
2. **Skills layer:** materialize each adopted portable-skills entry in the tooling's skill/instructions format, homed with the project it serves (estate-wide ones in the hub); with no tooling, keep them as printed checklists in the hub.
3. **Found the people project:** seed the register `people.md` per `corpus/connections.md`.
4. **Found the company-intelligence project:** seed `company.md` per the signal-log + four-register format in `corpus/company-watch.md`, pre-filling the leadership chain, direction surfaces, and initial themes the intake's company-baseline questions (`knowledge/week1-intake.md` §13) have already surfaced.
5. **Found the records project:** seed `worklog.md` + `timelog.md` per `corpus/work-record.md` and the reports dir per `corpus/work-report.md` (expected core-adopt at every policy outcome; the seed-refresh line in `corpus/boundary-protocol.md` is the one piece depending on A2). The PUBLIC view's home is an intake question (`knowledge/week1-intake.md` §15) — until it resolves, seed the staging file `worklog-public.md`; once a team surface is named, render there and retire the staging file.
6. **Found the health project:** seed the tracker `health.md` per `corpus/health-guard.md`, and wire the guard's clock from what Phase 1 found — the best reminder mechanism the device and sanctioned tooling offer (calendar blocks, OS/assistant break reminders, the agent's own surface; degraded path: phone timers + the printed moment table).
7. **Found the communication project:** seed `communication.md` per `corpus/communication-craft.md`.
8. **Found the risk project:** seed `risks.md` per `corpus/risk-register.md`.
9. **Portfolio board (hub state):** seed `projects.md` per the board format in `corpus/project-lifecycle.md`, pre-filling any candidates the intake's project-landscape questions (`knowledge/week1-intake.md` §12) have already surfaced. **Per-work-project homes are founded on demand at accept** (registered in the estate registry, dev record per `corpus/dev-workflow.md`) — never pre-seeded.
10. **Log:** write the unfold log in this clone's `local/` — date, ledger summary, the estate registry as founded, what was folded away.
11. **Report to the user:** the ledger answers, the estate as founded (each project + its home), and the single next action (typically: wire the hub's instructions file into the sanctioned tool, exact steps stated).

## Re-running

Run again from Phase 1 whenever policy or tooling changes at work, or the seed has been updated. Re-runs regenerate instruction/skill layers and append to the ledger; living project state and the estate registry's existing entries are never touched.

Post-install, the clone's ONLY role is this update channel: day-to-day work happens in the estate projects, never in the clone (design principle 19). If the update channel goes unused (A2 unreachable), the clone is deletable without loss.

## Degraded manual path (no AI tooling sanctioned, or policy cannot carry a multi-project estate)

The single-clone fallback — used only when the estate form genuinely cannot exist here (design principle 19), never as a convenience default:

1. Read the corpus modules; adopt them as personal working conventions in reading form.
2. Hand-create `local/state/TODO.md` and `NOW.md` in this clone; maintain them per `corpus/task-convention.md`.
3. Use the portable-skills entries as printed checklists.
4. Re-check the tooling policy occasionally; if an agent later becomes sanctioned, run the full unfold and found the estate.
