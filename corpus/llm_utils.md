# llm_utils — the LLM provider seam

*Work-stack infrastructure (estate registry kind: infrastructure): ONE seam between the estate's code and every LLM provider it uses, ported at end-state from the maintainer's proven layering (design principle 25; user decision 2026-08-24). `research-infrastructure.md` names the two stacks; this project is the WORK stack's seam. The personal stack's seam library (its setup step 3) is the same concept instantiated on the other stack — one concept, one instance per stack, never mixed (the never-cross rule).*

## Charter

- **One seam, providers behind it.** Every LLM call in the estate's own code — engine jobs, eval harnesses, judges, experiment pipelines — goes through this seam; no consumer imports a provider SDK directly. Providers = whatever the employer sanctions (internal gateways, sanctioned endpoints), discovered at intake (§17) and configured here. The extraction lesson this ports: several consumers each hand-rolling provider calls diverge silently and are re-unified later at real cost — the seam exists from the start instead.
- **Mechanics only:** routing, retries, structured-output handling, call logging. Model CHOICE policy (which model for which task) is the consumer's meaning, held in the consumer's config; the seam executes it.
- **Secrets from the employer's secret store only** (`engineering-standards.md` secrets hygiene); parameters in config, never in code.
- **Default provider = the sanctioned agent tooling's own account.** Where an automation's LLM step can run either through the sanctioned agentic tooling's own account/subscription or through a separately-billed API route, the tooling's account is the default; API routes are a deliberate, per-consumer config choice (cross-provider needs, cost caps), never the silent default.
- **Usage ledger:** every call appends to one durable usage log — the ample-budget posture (`work-engine.md`) spends freely, but spend is always observed, never estimated.
- **Layering — bottom of the infrastructure stack:** this seam knows providers and nothing else. No compute topology, no workflow state, no consumer semantics; `devices.md` and `autoflow.md` may consume it, never the reverse.

## Discover before build

The team almost certainly has incumbents — a model gateway, a sanctioned SDK, an eval platform's client. Incumbents sit BEHIND the seam as providers; they do not replace it. Intake (§17) resolves the build form: an incumbent already covering the seam layer → this project is a thin connector over it (config + the usage ledger, little more); a real gap → the seam is built per `engineering-standards.md`. If an existing open-source seam library fits and the OSS-dependency policy sanctions it, pinning it by version and keeping only work config here is the preferred form — with no contributions back from work context without the policy check.

## Founding gate

Founds at the FIRST code consumer (typically the first eval harness or engine job calling a model from code). Until then the charter stands as the design of record, and assistant-tooling calls ride the sanctioned tooling directly.
