# devices — the compute and device client

*Work-stack infrastructure: the estate's client for the compute and devices the job can reach — registry, dispatch, run state, and device knowledge (end-state form, user decision 2026-08-24). The employer provides the compute itself; what it does not provide is the estate's OWN view of it — what exists, how to submit, what is running where. That client-side estate is this project. Its seed lesson (maintainer provenance): granted compute with no client-side registry sits idle for days while work queues elsewhere.*

## Charter

- **Registry, single truth:** one row per compute target the work can use — cluster, managed training/eval service, quota pool: access mode, capacity and quota, eligibility, cost model. Granted-but-idle capability is named waste (`compensation.md` acquire-at-eligibility: quotas are claimed when eligible and then actually used).
- **Connectors + one dispatch seam:** per-target submission mechanics (job templates, CLI/SDK wrappers) behind one seam consumers call. Mechanics only — WHAT runs where (placement policy) is the owning project's meaning.
- **Run state:** what is running or queued from this estate — experiment, target, since when — so any session answers "what's running where" without shell archaeology.
- **Device knowledge:** the work machine's own runbooks (setup, recovery, environment quirks) live here too — knowledge about a device lives with the device estate.
- **Layering:** above `llm_utils.md` (may consume its route seams), below `autoflow.md` (the platform places workers through this seam).

**Boundary:** this project registers WORK compute only. The user's own clusters are their own estate, reached per `research-infrastructure.md` (its satellite registry holds that run state); the never-cross rule decides which side a workload belongs to before any dispatch.

## Discover before build

The incumbents here are strong (cluster schedulers, managed ML platforms) and sit BEHIND the seam: the registry and run state are almost always the real gap, the connectors thin wrappers over incumbent CLIs/SDKs. Intake (§17) resolves per target.

## Founding gate

Founds when the first work compute target beyond the laptop is granted (a quota, a cluster account). The registry row is written the day access lands.
