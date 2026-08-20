# Research infrastructure — the substrate for research from the work machine

*What research runs ON: LLM access, secrets, compute, and repo sync for research done from the work device. `research-workflow.md` is the method lane; this module is its substrate. Born of the graded-boundary ruling (design principle 17, settled 2026-08-15): the work machine may host the user's own research tooling where that benefits them — in revocable, exit-ready form (`device-return.md`).*

## Two stacks, chosen by content

Research from the work machine runs on one of two substrate stacks. **The CONTENT of the work picks the stack — never convenience, and never mixed within one flow:**

- **Work stack** — for anything employer-confidential: the employer's sanctioned LLM endpoints, the employer's secret store, employer compute. Discovered before built (design principle 10): the team almost certainly already has incumbents — model gateways, eval harnesses, a secrets solution, experiment infrastructure — found at intake (§17–§18). The seam DESIGN from `engineering-standards.md` (one seam module, providers behind it, parameters in config) applies only where a real gap exists.
- **Personal stack** — for the user's own research: their LLM seam library with their own API keys, their secret manager signed in on this device, clones of their private research repos, and their own compute (personally-controlled clusters — the user's resources, part of their own estate, never employer resources).

**The one never-cross rule:** employer-confidential content never runs through the personal stack — not through personal API accounts, personal repos, or personal compute (the standing IP rule: nothing from work leaves the employer). Where a flow is gray (e.g. non-confidential work content to an external endpoint), the work policy discovered at intake §18 decides — checked once, recorded in `local/ledger.md`, then followed; the default before the check is no.

## Personal-stack setup on the work machine

After intake §18 clears device policy, install in this order — every item entering in its **most revocable per-device form** and logged to the footprint register at the moment it lands (`device-return.md`):

1. **Secret manager:** device sign-in with device-scoped authorization. Highest-tail-risk vault classes (e.g. crypto keys) stay excluded from this device — real risk, zero work-machine benefit.
2. **Personal git access:** a per-device credential (fine-grained token or per-device SSH key) scoped to the repos actually worked on — never an account password, never a broad classic token. A lost device then costs one revocation; the account is untouched.
3. **LLM seam:** clone the user's seam library; it reads keys from the environment exactly as on their own machine — the secret manager IS the key sync, no re-wiring.
4. **Research repos:** clone the private engines (sync model below).
5. **Compute access:** credentials/config for the user's own clusters, same per-device revocable form.

## Sync: private engines, rendered interfaces, the work machine as client

The user's research projects live in their own estate as **private engine repos** — the full working home (code, experiments, notes, and state as their own conventions allow) — with any public repo of a project maintained as a **rendered interface**: generated one-way from the engine, never worked in directly. Consequences for this device:

- **Git IS the sync.** The work machine clones the private engines and syncs code, docs, and results by ordinary pull/push. Nothing is homed here: the work machine is a CLIENT of the user's research estate — every clone deletable at any moment at zero loss beyond an unpushed working day.
- **Push feasibility is an intake fact, never an assumption** (§18): whether the device and network actually permit pushing to the user's own git hosting. Until verified, treat clones as read-capable only and confirm the push leg with a trivial test commit before relying on it. If push is blocked, the work-machine copies degrade to read-only reference and the user's own machine remains the write home.
- **Work content never enters these repos.** A private-engine clone on the work device is the user's own estate visiting; committing anything work-derived into it would carry employer content out — the same one-way rule as this seed repo, applied to every such clone.

## Compute

The user's clusters are their own estate — the work machine dispatches to them as a client, under the same revocable-credential discipline. The user's own research runs there freely. Work-confidential experiments run there only if the employer's policy explicitly permits work content on non-employer compute — an intake §18 check, never a guess; the default before the answer is no.

## The satellite registry — the research project's standing state (design principle 20a)

The estate's **research satellite** project (principle 19 roster) stewards the user's own research presence on this device. Its state file, `local/state/research.md`, holds one row per element:

- **Clone roster** — each research repo present: name · form (public interface / private engine) · credential form with its footprint-register line (`device-return.md`) · push state (`push verified YYYY-MM-DD` after the test commit, else `read-only`) · last sync date.
- **Run state** — what is currently running or queued on the user's own compute from this device: which experiment, which cluster, since when; enough that any session can answer "what's running where" without shell archaeology.
- **Session residue** — per-project one-liners a cold session needs (in-flight branch, next command, how to verify), per the cold-resume convention (`task-convention.md`).

Steward boundary: **the satellite executes; it never governs.** Direction, portfolio judgment, and venue decisions live in the user's own estate; this project reads the clones and the user's word, works, and reports back through git. A work-side session never re-derives the user's research portfolio, priorities, or strategy from here. `research-workflow.md` remains the method lane for the research work itself, on either stack.

## Fold-away note

Core-adopt whenever intake §18 clears any personal-stack presence at all. At a fully-locked-down policy outcome the module folds to its work-stack half (incumbent discovery + seam design), which stands on its own.
