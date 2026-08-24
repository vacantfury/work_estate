# Engineering standards (portable)

Defaults for new code. Where the employer or team has an established practice — documented or not — the team practice wins; these fill the gaps and govern surfaces the team never sees plus genuine greenfield.

## Team reality first

- **The team's real standard may be documented nowhere.** Long-history teams carry conventions that are non-standard by outside measures, non-optimal, and recorded only in the code, its review history, and people's heads. Discover before writing: read the actual repos and a stretch of merged PRs, and ask teammates — where practice diverges from the written guide, the practice is the standard.
- **Conform by default, even where these defaults are objectively better.** On any team-visible surface, deviating toward "optimal" is a defect, not an improvement — it taxes reviewers and trust. Improving a team convention is a social act: earn standing first, then propose through the team's own channels; never land the change unilaterally.

## Python tooling

- Package/project manager: **`uv`** — lockfile `uv.lock` committed, dependencies in standard `[project]` tables of `pyproject.toml`. Linting/formatting: `ruff`.
- Don't migrate an existing repo off its established tooling without a concrete reason; match what the team standardized on.
- Scaffolding restraint: package layout and manager are safe day-one defaults; application frameworks (CLI, config system, orchestration, experiment tracking) are chosen deliberately per project, never assumed from habit or boilerplate.

## Parameters live in config, never as magic numbers

- Any tunable — thresholds, weights, periods, band mappings, model choices — goes in a config file (YAML default) from the start, with code reading it. Fail-safe defaults in code are fine, marked as fail-safes. Pure unit conversions and mathematical constants are the exception.
- **The categorical twin:** every closed vocabulary — taxonomy, category set, band mapping — carries a typed residual member (`unknown`/`other`) that fails toward attention rather than silent misclassification, plus a named revision signal for the vocabulary itself (e.g. the residual bucket growing past a stated share).
- **Every heuristic number carries a tuning path:** a heuristic value enters code/config only together with a named way to tune it against real data (eval set, backtest objective, measurement). The tuning harness may come later, but the tuning task is filed at introduction time — a knob nobody can improve from evidence is a defect.

## Prefer mature tools over reinventing

- If a mature library does the task well, use it; wrap it behind your own seam if a stable interface is needed. Custom code is reserved for the genuinely bespoke: no good tool exists, or it IS the project's differentiating core logic.
- Before building any capability, check what already covers it.
- Where research still leaves several credible candidates for a consequential choice, settle it by a small time-boxed pre-experiment per candidate — elimination by evidence, not debate (`dev-workflow.md`, choice tournaments).

## Size to the known end-state

- When sizing a capability, seam, standard, or structure, the default is the GENERAL form correct at the known end-state — never the narrow variant with a "prove it on one consumer first, widen later" rider. Narrow-first needs a named concrete risk the general form cannot carry (safety, irreversibility, genuine end-state uncertainty); consumer-count caution alone is never such a risk. Keep the load-bearing boundaries full-grade (gates, typed contracts); drop the conservatism riders. The estate's own infrastructure is founded this way (design principle 25).

## Testing (tiered by trigger)

- **Any code project at birth:** `tests/` + pytest as a dev dependency, with at least one smoke test. Notes/paper/exploratory repos carry no mandate.
- **Libraries consumed by others:** green tests gate every release; the mandatory kind is seam/contract tests — the release is the consumer contract, so the tests assert the contract.
- **Anything taking consequential actions** (spends money, sends outbound messages, mutates shared state): the gate/executor logic is test-covered, with fail-closed behavior verified by a test.
- House style: fast, deterministic, no-network, no-secrets; the suite passes on a fresh clone with no keys.

## Version control

- Commit in small verified units; commit-message style matches the repo's existing log (check it first).
- Solo repos work directly on main; branch only for risky/abandonable work or parallel isolation. Shared repos: changes to the collaborator-facing contract surface go via branch + PR. No long-lived branches — merge or delete.
- Released libraries version by SemVer tags (`vX.Y.Z`); tags are immutable — never moved or reused; the change that alters the consumer contract ships its tag in the same session.
- No force-push without explicit approval; never commit secrets; never rewrite shared history without collaborator acknowledgment.

## Secrets hygiene

- The universal interface is **environment variables**: code reads plain env vars (`os.environ`, pydantic-settings) — never a secrets file, never with knowledge of any particular secret store.
- No plaintext secret value ever exists in a repo — committed or gitignored. Secrets live in the sanctioned secret store and are injected into the process at launch.
- **Which store is the sanctioned one is decided by the environment's own documentation and resources, discovered at intake — never imported from outside.** A personal secret manager present on the machine serves only personal-stack content (`research-infrastructure.md`); work secrets live in the work environment's own store, whatever intake finds it to be.
- `.env`-style patterns stay gitignored as defense-in-depth even though such files should never exist with real values.
- When any key is rotated or revoked, the record in the secret store is updated in the same motion — the store stays the single source of truth.

## Authority levels (for agentic systems taking consequential actions)

- Three levels: **`mechanical`** (deterministic code) < **`judgment`** (judgment-bearing agent) < **`sovereign`** (the responsible human).
- Every action declares its required level in config; it runs iff the principal's clearance meets the gate, else it escalates. Assign by consequence: external / irreversible / costs money / contacts a real person → sovereign; judgment-bearing but reversible → judgment; pure computation → mechanical.
- **Single enforcement choke point:** every action routes through one dispatcher that reads the gates — if any path can invoke a gated action directly, the config is decorative. An audit log records principal + authorizer + timestamp per action.
- An escalation reaches the human as a one-decision package: exact plan, blast radius, recommendation, yes/no. Any material state change between approval and execution invalidates the approval.
- The literature basis for this design, plus the reversibility classes an escalation should name and the verification ladder for agent claims: `agent-reliability.md`.
