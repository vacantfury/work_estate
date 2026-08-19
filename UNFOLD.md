# UNFOLD — the installer

*Run on the work device, in the first session after cloning. Executable by any sanctioned capable agent — or manually by the user (degraded path at the end). This file is deliberately plain markdown with no dependency on any harness, language runtime, or feature: which AI tooling may execute it is itself a question it answers (A1).*

## Contract

- **Input:** this repo (read-only during the unfold), the work documents the user points at (AI-tooling policy, device/acceptable-use policy, engineering handbook if offered), and the device itself.
- **Output:** everything lands in `local/` (gitignored). The committed seed is never edited by the unfold, and nothing derived from employer docs, systems, or code is ever committed or pushed — the one-way flow rule (CLAUDE.md) is absolute.
- **Re-runnable:** `local/generated/` is wiped and regenerated on each run; `local/state/` (living work state) is never touched by a re-run.

## `local/` layout (created by the unfold)

- `local/ledger.md` — the resolved A1–A6 answers, each with its deciding evidence, dated; re-runs append a new dated section, keeping history.
- `local/generated/` — the unfolded convention set; safe to wipe and regenerate.
- `local/state/` — living work state (`TODO.md`, `NOW.md`, `archive.md`, notes); owned by daily work, not by the unfold.

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
- **A4 — form of the work-side task/state layer.** Default: `local/state/` inside this clone. If policy or practice prefers work content in a work-managed location, place the state there instead and record the pointer in the ledger.
- **A5 — applicable convention/skill subset.** Per corpus module and per portable-skills entry: **adopt / adapt / fold away**, one-line reason each. What is folded away stays in the corpus, available to later re-runs.
- **A6 — backup of the work-side local state.** `local/` never pushes anywhere, so it is single-copy until a route is chosen. Decide the backup process ONLY from what Phase 1 found: the work docs (what storage the policy sanctions for work-adjacent personal notes) and the tools actually available on the device (employer-managed folder sync, work-hosted git, device backup). Never a personal cloud or the personal remote — one-way flow is absolute. If A4 placed the state in a work-managed location, backup may already be inherited — record that as the answer. Nothing suitable found → record **unresolved** and note that `local/state/` is consciously single-copy until re-run.

## Phase 3 — generate

From the resolved ledger, wipe and regenerate `local/generated/`:

1. **Instructions layer (tier 1):** produce the always-loaded instructions file in the sanctioned tooling's native format — an agent-memory file, a repo instructions file, or (no tooling) a printable conventions one-pager. Content: the adopted corpus subset, adapted per A5, law only — no changing facts.
2. **Skills layer:** materialize each adopted portable-skills entry in the tooling's skill/instructions format; with no tooling, keep them as checklists in `local/generated/checklists/`.
3. **Task/state layer (tier 3):** seed `local/state/TODO.md` (`# TODO (ordered)`) and `local/state/archive.md` **if absent** — an existing state file is never overwritten.
4. **Session board (tier 2):** seed `local/state/NOW.md` if absent.
5. **Reports dir:** seed `local/state/reports/` if absent, per `corpus/work-report.md` (expected core-adopt at every policy outcome; the seed-refresh line in `corpus/boundary-protocol.md` is the one piece depending on A2).
6. **Portfolio board:** seed `local/state/projects.md` if absent, per the board format in `corpus/project-lifecycle.md`, pre-filling any candidates the intake's project-landscape questions (`knowledge/week1-intake.md` §12) have already surfaced. Per-project dev records (`local/state/projects/<name>.md`, per `corpus/dev-workflow.md`) are created on demand when a project goes active — never pre-seeded.
7. **Company-watch store:** seed `local/state/company.md` if absent, per the signal-log + four-register format in `corpus/company-watch.md`, pre-filling the leadership chain, direction surfaces, and initial themes the intake's company-baseline questions (`knowledge/week1-intake.md` §13) have already surfaced.
8. **Health tracker:** seed `local/state/health.md` if absent, per the tracker format in `corpus/health-guard.md`, and wire the guard's clock from what Phase 1 found — the best reminder mechanism the device and sanctioned tooling offer (calendar blocks, OS/assistant break reminders, the agent's own surface; degraded path: phone timers + the printed moment table).
9. **Work record:** seed `local/state/worklog.md` if absent, per the private-record format in `corpus/work-record.md`. The PUBLIC view's home is an intake question (`knowledge/week1-intake.md` §15) — until it resolves, seed the staging file `local/state/worklog-public.md`; once a team surface is named, render there and retire the staging file.
10. **Work-engine registry + lane state:** seed the agent-jobs registry `local/state/agent-jobs.yaml` if absent, per the schema in `corpus/work-engine.md`, with priorities/cadences drafted from the corpus defaults and the queue mode set from A1 + intake §17 (scheduled agents · session-opening sweep · degraded checklists); seed `local/state/people.md` (per `corpus/connections.md`) and `local/state/communication.md` (per `corpus/communication-craft.md`) if absent.
11. **Footprint register:** seed `local/state/footprint.md` if absent, per `corpus/device-return.md`, and back-fill a line for anything personal already present on the machine (this clone itself needs no line while the repo is public and credential-free; the first of the user's credentials or sign-ins does).
12. **Log:** write `local/generated/UNFOLD-LOG.md` — date, ledger summary, what was generated where, what was folded away.
13. **Report to the user:** the ledger answers, what was generated, and the single next action (typically: wire the generated instructions file into the sanctioned tool, exact steps stated).

## Re-running

Run again from Phase 1 whenever policy or tooling changes at work, or the seed has been updated. Re-runs regenerate `local/generated/` only, append to the ledger, and never touch `local/state/`.

## Degraded manual path (no AI tooling sanctioned)

1. Read the corpus modules; adopt them as personal working conventions in reading form.
2. Hand-create `local/state/TODO.md` and `NOW.md`; maintain them per `corpus/task-convention.md`.
3. Use the portable-skills entries as printed checklists.
4. Re-check the tooling policy occasionally; if an agent later becomes sanctioned, run the full unfold.
