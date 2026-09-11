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
- **Before building any capability or attacking any complex problem, search for what already exists — tools AND results.** Tools: something may already do the task. Results: someone may already have answered the question — a prior experiment, a published measurement, an existing analysis — making the build unnecessary. The search precedes the design, not the review.
- **"Existing" spans both worlds: the open ecosystem and the employer's internal one.** Internal libraries, services, platforms, shared repos, other teams' solutions, and internal prior art (docs, experiment results, postmortems) count as available exactly the way open-source does — search both before writing code. Where the two tie, the internal tool wins: it comes with its owners, its support channel, and its compliance posture already settled.
- Where research still leaves several credible candidates for a consequential choice, settle it by a small time-boxed pre-experiment per candidate — elimination by evidence, not debate (`dev-workflow.md`, choice tournaments).

## Size to the known end-state

- When sizing a capability, seam, standard, or structure, the default is the GENERAL form correct at the known end-state — never the narrow variant with a "prove it on one consumer first, widen later" rider. Narrow-first needs a named concrete risk the general form cannot carry (safety, irreversibility, genuine end-state uncertainty); consumer-count caution alone is never such a risk. Keep the load-bearing boundaries full-grade (gates, typed contracts); drop the conservatism riders. The estate's own infrastructure is founded this way (design principle 25).

## Testing (tiered by trigger)

- **Controls before tests.** Where a deterministic control is possible, install the control and test it. Permission backstops, live-session guards, and configured spend limits act before the consequential call (`agent-reliability.md` §One permission policy); a test never substitutes for an enforceable control.
- **Code projects at birth:** a Python package starts with `tests/`, pytest as a dev dependency, one meaningful smoke test, and the standard block below. Use the stack's equivalent for other languages. Notes, papers, and exploratory experiment code carry no blanket test mandate.

```toml
[tool.pytest.ini_options]
testpaths = ["tests"]
markers = [
    "live: requires network access or keys",
    "slow: excluded from the fast suite",
    "eval: model evaluation, selected explicitly",
    "quarantine: known flaky; excluded from unattended test alerts",
]
addopts = "-m 'not live and not slow and not eval'"
```

- **Fast and keyless by default:** `uv run pytest` passes on a fresh clone without network access or keys. Select live, slow, and eval runs deliberately. Quarantine is a known-flaky label, not permission to hide a failure from a release check; a scheduled test-alert job excludes that marker.
- **Versioned seams carry the strongest duty.** The release gate runs the keyless suite directly against the exact current tree before cutting a tag or release, and refuses on red or a gate error. Seam/contract tests are mandatory: the tag is the consumer contract. Providers ship explicit test helpers for consumers where useful, never auto-registered plugins; helper contract changes follow SemVer.
- **Narrow CI:** versioned infrastructure runs the keyless suite on push and tag in a fresh checkout. Other projects add CI when shared maintenance or a consumed interface needs it, following the team's pipeline.
- **Consequential actions:** gate/executor logic is covered, including fail-closed paths. A fixed implementation defect gets a regression check against its observed failure mode, not a test that merely repeats the implementation.
- **Substantive builds get an independent review before completion is reported.** Triage findings before declaring done; mechanical edits are exempt. Cross-family review and immutable review inputs follow `human-agent-collaboration.md` §Two agents. Model evals remain judged signals and never replace deterministic controls.

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
- **Secret values never appear in output.** Diagnostics, logs, and error reports never dump the raw environment or process table (`env`, `ps eww`, config dumps) — inherited variables leak exactly this way; print variable names, mask values. A value that has reached any output, transcript, or pasted snippet is treated as exposed: rotate it, then fix the leak path.
- **Agents and automation handle secret NAMES, never values.** Agent tooling references secrets by variable name; values are injected at process launch outside the agent's view. An agent never reads a value back, echoes it, or writes it to a file.
- **Headless runs authenticate as a machine identity.** Scheduled jobs, CI, and cluster runs use the environment's sanctioned machine identity (service principal, managed identity, service account) at least-privilege — read-only where read-only serves — created once and reused, never a fresh ad-hoc token per project; its credential lives outside every repo.
- **A repo documents the env-var names it needs** — in the README or config module, or a placeholder example file where the team convention uses one. Names and shapes, never values: this is the contract a fresh clone sets up against.

## Authority levels (for agentic systems taking consequential actions)

- Three levels: **`mechanical`** (deterministic code) < **`judgment`** (judgment-bearing agent) < **`sovereign`** (the responsible human).
- Every action declares its required level in config; it runs iff the principal's clearance meets the gate, else it escalates. Assign by consequence: external / irreversible / costs money / contacts a real person → sovereign; judgment-bearing but reversible → judgment; pure computation → mechanical.
- **Single enforcement choke point:** every action routes through one dispatcher that reads the gates — if any path can invoke a gated action directly, the config is decorative. An audit log records principal + authorizer + timestamp per action.
- An escalation reaches the human as a one-decision package: exact plan, blast radius, recommendation, yes/no. Any material state change between approval and execution invalidates the approval.
- The literature basis for this design, plus the reversibility classes an escalation should name and the verification ladder for agent claims: `agent-reliability.md`.
