# Research infrastructure — the substrate for research from the work machine

*What research runs ON: LLM access, secrets, compute, and repo sync for research done from the work device. `research-workflow.md` is the method lane; this module is its substrate. Born of the graded-boundary ruling (design principle 17, owner rulings 2026-08-15): the work machine may host personal-estate research tooling where that benefits the owner — in revocable, exit-ready form (`device-return.md`).*

## Two stacks, chosen by content

Research from the work machine runs on one of two substrate stacks. **The CONTENT of the work picks the stack — never convenience, and never mixed within one flow:**

- **Work stack** — for anything employer-confidential: the employer's sanctioned LLM endpoints, the employer's secret store, employer compute. Discovered before built (design principle 10): the team almost certainly already has incumbents — model gateways, eval harnesses, a secrets solution, experiment infrastructure — found at intake (§17–§18). The seam DESIGN from `engineering-standards.md` (one seam module, providers behind it, parameters in config) applies only where a real gap exists.
- **Personal stack** — for the owner's own research: his LLM seam library with his own API keys, the personal secret manager signed in on this device, clones of his private research repos, and his own compute (personally-controlled clusters — his resources, part of his personal estate, never employer resources).

**The one never-cross rule:** employer-confidential content never runs through the personal stack — not through personal API accounts, personal repos, or personal compute (the owner's own IP rule: nothing from work leaves the employer). Where a flow is gray (e.g. non-confidential work content to an external endpoint), the work policy discovered at intake §18 decides — checked once, recorded in `local/ledger.md`, then followed; the default before the check is no.

## Personal-stack setup on the work machine

After intake §18 clears device policy, install in this order — every item entering in its **most revocable per-device form** and logged to the footprint register at the moment it lands (`device-return.md`):

1. **Secret manager:** device sign-in with device-scoped authorization. Highest-tail-risk vault classes (e.g. crypto keys) stay excluded from this device — real risk, zero work-machine benefit.
2. **Personal git access:** a per-device credential (fine-grained token or per-device SSH key) scoped to the repos actually worked on — never an account password, never a broad classic token. A lost device then costs one revocation; the account is untouched.
3. **LLM seam:** clone the owner's seam library; it reads keys from the environment exactly as on the personal machine — the secret manager IS the key sync, no re-wiring.
4. **Research repos:** clone the private engines (sync model below).
5. **Compute access:** credentials/config for the owner's own clusters, same per-device revocable form.

## Sync: private engines, rendered interfaces, the work machine as client

The owner's research projects live in his own estate as **private engine repos** — the full working home (code, experiments, notes, and state as his estate's conventions allow) — with any public repo of a project maintained as a **rendered interface**: generated one-way from the engine, never worked in directly. Consequences for this device:

- **Git IS the sync.** The work machine clones the private engines and syncs code, docs, and results by ordinary pull/push. Nothing is homed here: the work machine is a CLIENT of the personal research estate — every clone deletable at any moment at zero loss beyond an unpushed working day.
- **Push feasibility is an intake fact, never an assumption** (§18): whether the device and network actually permit pushing to personal git hosting. Until verified, treat clones as read-capable only and confirm the push leg with a trivial test commit before relying on it. If push is blocked, the work-machine copies degrade to read-only reference and the personal machine remains the write home.
- **Work content never enters these repos.** A personal-engine clone on the work device is personal estate visiting; committing anything work-derived into it would carry employer content out — the same one-way rule as this seed repo, applied to every personal clone.

## Compute

The owner's clusters are personal estate — the work machine dispatches to them as a client, under the same revocable-credential discipline. His own research runs there freely. Work-confidential experiments run there only if the employer's policy explicitly permits work content on non-employer compute — an intake §18 check, never a guess; the default before the answer is no.

## Fold-away note

Core-adopt whenever intake §18 clears any personal-stack presence at all. At a fully-locked-down policy outcome the module folds to its work-stack half (incumbent discovery + seam design), which stands on its own.
