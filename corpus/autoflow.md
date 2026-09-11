# autoflow — the automation platform

*Work-stack infrastructure: the runtime that EXECUTES the engine's standing jobs — the mechanics of the agent-jobs layer as a project of its own (mechanics/meaning split, end-state form; user decision 2026-08-24). `work-engine.md` remains the composition module and the registry's home: WHICH jobs exist, their lanes, escalation rules, and gates are the engine's meaning. HOW they run is this platform.*

## Charter

- **Scope:** scheduler · cycle runtime · worker dispatch (headless runs of the sanctioned agent tooling) · the run ledger (every job run: id, started, outcome, spend, output home) · liveness mechanics (the `marker`/`silence_h` checks the autonomy gradient's axis 3 declares).
- **Mechanics only, gates untouched:** the platform never owns a job's meaning (that stays with the lane) and never lowers a gate — `gate` fields and the prepare-only rails ride through it unchanged (`work-engine.md` rails; `agent-reliability.md` irreversibility).
- **Where it runs:** entirely on the work account's sanctioned tooling and budget. It consumes `devices.md` for worker placement wherever compute beyond the laptop exists, and `llm_utils.md` for direct model calls.

## The cycle pattern (canonical here; moved from `work-engine.md`)

Scheduled lanes run plan → execute → collect → report as CYCLES: the user's attention is batched at cycle boundaries (one consolidated report and choice surface per cycle, never a drip), and each cycle's results feed the next cycle's priorities and budget split — measured value reallocates budget, drift never does.

## Isolate, then promote

Automated work runs in an isolated workspace and enters the main state only through checked promotion. For repo changes, **one unit = one git worktree and branch = one ledger row = one atomic promote-or-discard decision**. Keep units independently attributable. A validated append-only record may use a checked append instead. Effects on the world cannot be isolated by a branch, so such a unit stages an inert artifact and waits at the user's gate. Unclassifiable effects take that gated path and are logged for review of the effect vocabulary.

1. **Dispatch with scope and authority.** The task's home, acceptance checks, result class, and executor are explicit. Per-action authorization governs the run itself; the promotion gate governs only its artifact. A worktree never authorizes a mid-run send, spend, registration, or other consequential effect.
2. **Check the complete result.** Validate contracts, schemas, invariants, and relevant registry consistency as well as the diff. Deterministic checks support mechanical promotion; a model-only review stays judged and follows the appropriate review gate. Recurring reasons for manual review enter the validator backlog.
3. **Serialize promotion.** Each candidate enters a merge queue, rebases onto the then-current main, and reruns the whole-state checks before promotion. Two independently green branches may be jointly broken. A moving base invalidates the earlier result; per-branch-only checks never authorize the merge.
4. **Protect the checks.** A diff touching its own checks or gate cannot auto-merge under those checks. Escalate one authority tier unconditionally; a top-tier gate stays with the user. Record the changed check surface and independent review evidence.
5. **Finish the unit within its cycle.** Promote it under its gate, or discard the candidate and record the reason, evidence, and any re-planned task. No branch drifts into another cycle through sunk cost. Discarding a candidate never erases the run ledger or silently closes the underlying obligation.

**With ample budget, verified-merge throughput is the scarce resource.** Throttle dispatch by a work-in-progress cap sized to the check and merge queue, not by spend. Put spare compute into redundant verification and adversarial checkers. Redundancy carries deliberate variance in model family, framing, or decomposition; identical replicas share failure modes. Keep the WIP cap and check-suite selection in installed config, with queue depth, check latency, rejected promotions, and escaped defects as the tuning data. If budget actually binds, the existing queue budget still applies; authority never changes with budget.

## Runtime adaptation (canonical here; resolved by unfold A1)

- *Full agent harness with scheduled runs sanctioned* → jobs run as actual scheduled/background workers.
- *Assistant-only tooling, or unattended runs not sanctioned* → the registry becomes the **session-opening sweep**: each working session starts by running the due jobs' procedures inline, highest priority first, time-boxed.
- *No sanctioned tooling (degraded path)* → the lanes survive as session disciplines and printed checklists; the registry documents intent for a later re-run.

## Founding gate

Founds at the first sanctioned scheduled/unattended job (the autonomy gradient's trigger 1). Before that, the session-opening sweep is convention and needs no platform.
