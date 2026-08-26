# Applied-science playbook (LLM product features)

How an applied scientist on an LLM copilot/product team works well, distilled from public practitioner canon and platform engineering write-ups (sources: `knowledge/role-workflow-research.md`). **Provisional by provenance:** written pre-start from public sources (axis 2 of the build model — `text_docs/design.md`); every convention here yields to the team's actual established practice, and the unfold treats each section as adopt / adapt / fold-away like any other module.

## Working posture

- **Error analysis first, evals second.** Don't write evals against a spec; ship a minimal end-to-end version, generate real transcripts, and read them. The failure taxonomy discovered in real data decides which evaluators are worth building at all.
- **Offline evals are a failure filter, never a ship signal.** They gate iteration and CI; only online experiments with guardrail metrics decide shipping.
- **Spending most development time on error analysis and evaluation is the job, not overhead.** Strong practitioners report 60–80%.
- **Read the data yourself.** Error analysis is never outsourced and never delegated to an LLM before a human has read the first 30–50 traces — it is the feedback loop between product understanding and the eval suite.
- **Safety/responsible-AI review is part of the shipping loop,** not a parallel process: automated guardrail metrics are its always-on layer, human impact review its judgment layer.
- **Calibrate to the team's actual bar.** Reliable, predictable delivery against agreed expectations beats sporadic heroics: scope commitments conservatively, renegotiate early when reality shifts, and spend scarce attention only where judgment is required — automate or template the rest. Over-commitment, not under-ambition, is this role's classic failure mode.
- **The health floor binds before the bar.** Sustainable delivery and minimal-time efficiency are optimized strictly inside the user's hard health floors — sleep, real meals, the hard daily stop, movement cadence, symptoms-outrank-commitments (`health-guard.md`); no commitment, deadline, or review cycle buys a floor. On-call duty is the one carve-out through the work/personal wall.

## The three loops

- **Daily:** read a handful of fresh transcripts; note surprises; log failures before they compound.
- **Per feature:** minimal V0 → real data → error analysis (open coding → taxonomy, to saturation) → evaluators for observed failure modes only, cheapest form first (assertion → reference-check → LLM-judge) → calibrate judges → iterate with the harness re-scoring every change.
- **Per release:** offline suite as CI gate → safety/RAI review → internal canary → flighted experiment (guardrails as constraints, metrics declared upfront) → ramp → production monitoring feeding back into error analysis.
- These loops are the LLM-product instantiation of the general staged funnel (`dev-workflow.md`) — design → decision-point tournaments by pre-experiment → comparable variants → the environment ladder; the per-release loop IS its production rung.

## Conventions

- **Eval sets:** built from real traces, not synthetic; keep a capability suite (low pass rate, hill-climbing) separate from a regression suite (stays ~100%); graduate mastered capabilities into regression; refresh on a 2–4 week cadence and after any model/prompt change or incident. A saturated eval (100% pass) has stopped providing signal — raise difficulty rather than celebrate.
- **LLM judges:** binary pass/fail over Likert scales; calibrated against human labels (TPR/TNR + inter-rater agreement) before being trusted, and re-checked on maintenance cadence; position-bias controlled on pairwise comparisons; always given an "Unknown" escape hatch; one judge per dimension rather than one monolithic grader. Literature limits of judges (same-family self-bias, trajectory-judging weakness) and when a real checker must replace one: `agent-reliability.md`.
- **Experiments:** primary/secondary/guardrail metrics declared before launch — no post-hoc metric shopping; guardrails (quality floors, latency, cost) enforced as constraints, not optimized; check tail effects, not just averages; every experiment closes with a written readout and an explicit ship/hold/kill call.
- **Changes:** every prompt/retrieval/model change re-runs the regression suite against the last passing baseline; a provider model swap re-runs everything — behavior shifts under stable prompts.
- **Escalation ladder for capability gaps:** prompt engineering → retrieval/grounding → fine-tuning → distillation; escalate only when the cheaper layer provably hits a wall.
- **Post-training (SFT/RL) rides the same eval spine:** training-data provenance recorded; eval sets strictly held out of every training mix; reward models/judges calibrated like any judge; every checkpoint scored against capability + regression suites before promotion; reward hacking / metric gaming watched as a standing failure mode.

## Model-migration discipline

For a copilot product shipping on successive model generations across providers, migration is a first-class recurring workflow, not an occasional chore:

- **Every candidate model is a full regression event.** Capability and regression suites re-run from scratch; behavior is never assumed to transfer under a stable prompt — variance and tail behavior shift most in metrics close to raw model output.
- **Keep the model seam provider-agnostic** (the publicly documented copilot pattern: a proxy/abstraction layer that swaps models without product-code changes), so evaluation, canary, flighting, and rollback are uniform across providers.
- **Declare the qualification bar before evaluating:** which capability gains justify migrating, which regressions block, with cost and latency weighed alongside quality — the decision is a trade, and the readout states it as one.
- **Prompts and scaffolds are model-coupled.** Migration includes re-tuning prompts per model family; per-model variants stay versioned, and the outgoing model's configuration stays restorable until the ramp completes.
- **The swap ships like any feature:** canary → flighted experiment with guardrails → ramp, closing with a written readout (see `portable-skills.md` experiment-readout).

## Working in the org

Relationship and expectation work is first-class, not overhead around the "real" job:

- **Manager alignment is the primary loop.** Week 1: agree what solid performance at level looks like in the review framework's own terms; thereafter keep a running shared record of delivered work — the review conversation should hold no surprises in either direction. The mechanism is the work record's public view (`work-record.md`): rendered from the private day-by-day record, homed wherever intake finds the team actually posts and reads status.
- **Deliberate relationship investment.** Regular 1:1s beyond the manager: skip-level where welcomed, the senior scientists on the team, and the cross-team partners the charter actually depends on. Trust built early is cheap; trust needed late is expensive.
- **Visibility is part of shipping.** Work is done when the people it matters to know about it — short demos, sprint readouts, written summaries in the channels leadership actually reads; let the artifacts (readouts, docs) do the broadcasting.
- **Predictability is the reputation to build.** Communicate status honestly and early, especially on slips; a reliably-forecasting scientist earns autonomy.
- **Presence calibrates to the real norm and is spent deliberately.** Discover the actual on-site practice — the written policy AND what teammates really do (days attended, hours kept, how presence is read) — rather than assuming from the policy text; attend at the level within that real norm that fully serves delivery and the relationship map, not above it by default, and make attended time count by concentrating the presence-dependent work (1:1s, demos, informal relationship building) onto on-site days.
- **Team conventions are conformed to first, improved (maybe) later — in that order.** A long-history team's conventions may be non-standard, non-optimal, and documented nowhere; discover the real ones the same way as presence (official docs AND the artifacts — code, merged PRs, review threads — AND teammates directly), follow them on every team-visible surface even where a better way is known, and learn the why from the people who carry the history before ever proposing change. Convention change is a social act: earn standing, then propose through the team's own channel — never unilateral cleanup.
- **Projects are chosen, not only executed.** What is worked on determines delivered impact more than execution quality, so the whole project arc — sourcing candidates, gathering intelligence (including asking people), deciding, negotiating, initiating own work via PoC, syncing and presenting, landing at a declared end — runs as a standard workflow on a standing pipeline: `project-pipeline.md`. Selection power is earned; early tenure delivers assigned work reliably while the pipeline runs in the background.
- **The company is watched, not assumed.** A standing watch (`company-watch.md`) keeps a graded, longitudinal picture of leadership and high-level people across the whole company — the own org watched most closely, but proximity weights attention, never draws the boundary: what they formally lead, visibly push, and casually signal; who is promoted or departs and for what (distilled into the reward map — what the company actually rewards and penalizes, the sharpest behavior calibration there is); and the direction it adds up to, themes tracked with trajectory (emerging/rising/established/fading). The record is candid and complete, for the user's benefit. Work re-aims toward it through the cheapest sufficient rung: reframe the narrative first, reshape scope next, re-bet the portfolio only on the strongest evidence, and pre-position skills and relationships early on rising themes and rising people.
- **Human-agent collaboration includes the whole team.** The target is the best work result through the best collaboration between agents and ALL the humans in the loop — teammates, reviewers, cross-team partners, not just oneself. Agent-assisted work is written for the colleague who reviews and maintains it: team idiom, reviewable sizes, no alien scaffolding. The team's actual norms on AI use (what's sanctioned, what's disclosed, how AI-assisted work is received in review) are discovered at intake and followed; agent output pace calibrates to what the human review loop can absorb — flooding reviewers is a collaboration failure, not productivity. Where colleagues run their own agents, prefer conventions that keep mixed human/agent work legible to everyone.

## Procedures

The recurring procedures backing this playbook live in `portable-skills.md`: **error-analysis**, **judge-calibration**, **experiment-readout** (plus the general **results-triage** and **systematic-debugging**).
