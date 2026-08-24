# autoflow — the automation platform

*Work-stack infrastructure: the runtime that EXECUTES the engine's standing jobs — the mechanics of the agent-jobs layer as a project of its own (mechanics/meaning split, end-state form; user decision 2026-08-24). `work-engine.md` remains the composition module and the registry's home: WHICH jobs exist, their lanes, escalation rules, and gates are the engine's meaning. HOW they run is this platform.*

## Charter

- **Scope:** scheduler · cycle runtime · worker dispatch (headless runs of the sanctioned agent tooling) · the run ledger (every job run: id, started, outcome, spend, output home) · liveness mechanics (the `marker`/`silence_h` checks the autonomy gradient's axis 3 declares).
- **Mechanics only, gates untouched:** the platform never owns a job's meaning (that stays with the lane) and never lowers a gate — `gate` fields and the prepare-only rails ride through it unchanged (`work-engine.md` rails; `agent-reliability.md` irreversibility).
- **Where it runs:** entirely on the work account's sanctioned tooling and budget. It consumes `devices.md` for worker placement wherever compute beyond the laptop exists, and `llm_utils.md` for direct model calls.

## The cycle pattern (canonical here; moved from `work-engine.md`)

Scheduled lanes run plan → execute → collect → report as CYCLES: the user's attention is batched at cycle boundaries (one consolidated report and choice surface per cycle, never a drip), and each cycle's results feed the next cycle's priorities and budget split — measured value reallocates budget, drift never does.

## Runtime adaptation (canonical here; resolved by unfold A1)

- *Full agent harness with scheduled runs sanctioned* → jobs run as actual scheduled/background workers.
- *Assistant-only tooling, or unattended runs not sanctioned* → the registry becomes the **session-opening sweep**: each working session starts by running the due jobs' procedures inline, highest priority first, time-boxed.
- *No sanctioned tooling (degraded path)* → the lanes survive as session disciplines and printed checklists; the registry documents intent for a later re-run.

## Founding gate

Founds at the first sanctioned scheduled/unattended job (the autonomy gradient's trigger 1). Before that, the session-opening sweep is convention and needs no platform.
