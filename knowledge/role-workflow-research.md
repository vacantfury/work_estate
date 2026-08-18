# Role & workflow research — the axis-2 digest

*Axis-2 output (see `text_docs/design.md`, four-axis build model): pre-start, public-source research on the role archetype — an applied scientist on an LLM copilot/product team — and the environment such a role likely operates in. Researched 2026-08-04. Everything here is PROVISIONAL by construction: publicly documented facts are labeled with sources; everything else is assumption, and every assumption is meant to be confirmed or refuted at intake (axis 3) via `week1-intake.md`. Nothing here derives from employer-internal material.*

*Source-strength labels: `[documented: URL]` = official/primary source · `[reported: URL]` = third-party reporting, verify on the ground · `[practitioner-consensus]` = widely repeated practitioner canon · `[inferred]` = reasoning, no direct source.*

## Part 1 — The role archetype

What public sources say an applied scientist in a large-company LLM copilot org owns. No official first-party description of role scope, leveling, or team process was found — this part leans on job postings, official planning docs, and third-party/crowdsourced HR sources, each flagged.

### 1.1 What job postings say the role owns

Recurring responsibility categories across Applied Scientist postings into the M365 Copilot org (Applied Scientist II · Senior Applied Scientist / Copilot & Agents Core): **(a)** orchestrator/agent reasoning work; **(b)** model training (fine-tuning, reinforcement learning); **(c)** retrieval/ranking for grounding in enterprise data (dense/sparse hybrid, late-interaction architectures); **(d)** evaluation, metrics, and A/B testing infrastructure; **(e)** shipping features from concept to production, in explicit partnership with engineering and product [documented: https://aijobs.net/job/1381387-applied-scientist-ii-m365-copilot/ · https://flexa.careers/jobs/microsoft-senior-applied-scientist-6a296f8c15389bc9e82c593f]. The public orchestrator documentation (reasoning loop: safety checks → context/tool selection → invocation → synthesis → RAI-gated response) substantiates what "advance orchestrator reasoning" maps to [documented: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/orchestrator].

### 1.2 Leveling context

Public leveling data conflicts and no official map exists. Crowdsourced ladder tables put L61–62 as the "II" band with L63 the first "Senior"-titled level on the general engineering ladder; weaker anecdotal evidence suggests the applied-science/research track runs numerically one level "hotter" than the engineering ladder for equivalent seniority. **Unresolved by public sources** — the practical takeaway is to calibrate scope expectations with the manager directly, not from forum tables [documented: https://shiftmag.dev/microsofts-software-engineering-career-ladder-9318/ · levels.fyi/Blind summaries, all self-reported data].

### 1.3 Work split and culture signals

No first-person "day in the life" account by an applied scientist in this org was found. Composite from posting language: applied ML research + production ML engineering (pipelines, eval harnesses) + analysis + heavy cross-functional coordination, with posting emphasis ("concept to production", "scalable pipelines", "partnering") suggesting the balance tilts toward engineering and coordination over pure research [inferred]. Anonymous forum accounts describe a high-urgency shipping culture and heavy workload on AI teams, with visibility/growth upside cited as the offset — unverified anecdote, not fact [reported: Blind threads].

### 1.4 How impact is assessed

The performance system ("Connect") runs on **impact over activity**, self-reported against three circles: individual accomplishments · contributions to others' success · results built on others' work — the third circle explicitly rewards leveraging the org rather than reinventing. Cadence: Connects at least twice yearly, formal cycle May–August. Security-related contribution is an explicit evaluation input company-wide (since 2024). Level-specific expectations are not public — a manager conversation in week 1 ("what does great impact look like at this level, against the three circles") is the only reliable calibration [documented: https://www.deel.com/blog/employee-performance-reviews-at-microsoft/ · https://www.promotions.fyi/company/microsoft/performance-review — third-party HR sources, not official].

### 1.5 Planning rhythms

Microsoft's own published planning model (from its DevOps org, presented as representative practice — not confirmed for any specific org): 3-week sprints → ~9-week plans → 6-month seasons → 12-month strategies; cross-disciplinary self-managing teams of 8–12 with 12–18-month charters; a sprint-end mail ritual (what was accomplished, what's next); a hard bug cap (engineers × 5) halting feature work when exceeded; OKRs with outcome metrics only — activity proxies (lines of code, velocity, hours) explicitly rejected as key results [documented: https://learn.microsoft.com/en-us/devops/plan/how-microsoft-plans-devops]. Treat as the default expectation to verify, not fact about the specific team.

## Part 2 — The workflow canon: eval-driven development for LLM product features

How strong teams build LLM copilot/assistant features in 2025–2026, per practitioner canon (Hamel Husain, Eugene Yan, Shreya Shankar) and lab/platform engineering blogs (OpenAI, Anthropic, GitHub, Microsoft).

### 2.1 The mental model

Strong teams do **not** start by writing evals against a spec. They ship a minimal end-to-end system, generate real transcripts, and read them — **error analysis first, evals second** — building a failure taxonomy that decides which evaluators are worth building at all [documented: https://hamel.dev/blog/posts/evals-faq/]. Offline evals then gate iteration and CI, but are a **failure filter, not a ship signal** — only online experiments with guardrail metrics decide shipping [documented: https://www.growthbook.io/blog/how-to-a-b-test-ai-a-practical-guide]. Responsible-AI review is embedded as checkpoints inside the same workflow, not a parallel ethics process. Practitioners report **60–80% of development time goes to error analysis and evaluation**, not infrastructure [documented: hamel.dev evals FAQ].

*(Noted disagreement in the canon: Hamel advises against writing evals before building except for narrow well-specified constraints; Anthropic's agent guidance recommends defining capability evals before the agent can pass them. Both agree evals must be grounded in real/anticipated failure modes, never academic benchmarks; the split is open-ended features vs well-specified agent tasks [documented: hamel.dev evals FAQ · https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents].)*

### 2.2 The three loops

**Inner loop (daily):** read fresh production/dev transcripts; note surprises; log failures before they compound. Weekly: sample 10–20 outlier traces (latency spikes, retries, auto-flagged, user-reported).

**Per-feature loop:** minimal V0 system → assemble real data (production traces over synthetic — synthetic defects are unrealistic) → **error analysis**: open coding (free annotation) → axial coding (failure taxonomy + frequency), stop at saturation (~20 consecutive traces with no new category; ~100+ traces minimum) → build evaluators only for discovered failure modes, cheapest first (assertions/regex → reference-based → LLM-judge) → calibrate judges against human labels → map eval scores to business impact so thresholds are principled → iterate, re-running the harness on every change [documented: hamel.dev evals FAQ · https://developers.openai.com/cookbook/examples/partners/eval_driven_system_design/receipt_inspection · https://eugeneyan.com/writing/product-evals/].

**Per-release loop:** offline suite as CI gate → RAI/safety review (impact assessment, red-team) → internal canary/dogfood → flighted online experiment (1–5% enrollment; guardrail metrics with sequential testing; never change flag values mid-experiment) → ramp → production monitoring feeding back into error analysis. GitHub Copilot's public pipeline: 4,000+ offline tests in CI, live internal canary cohorts, a proxy layer to swap models without product-code changes [documented: https://github.blog/ai-and-ml/generative-ai/how-we-evaluate-models-for-github-copilot/].

### 2.3 Load-bearing procedure details

- **Eval-set construction:** build from real production traces; target ~50–100 failing cases within 200+ labeled samples; 75/25 dev/test split; one evaluator per dimension, combined by simple heuristics. Keep **capability suites** (low pass rate, hill-climbing) separate from **regression suites** (must stay ~100%); graduate mastered capability evals into regression. Refresh every 2–4 weeks and after any model/prompt change or incident. A 100% pass rate means the eval stopped providing signal — raise difficulty; ~70% indicates a healthy stress-testing set [documented: eugeneyan.com/writing/product-evals/ · anthropic.com/engineering/demystifying-evals-for-ai-agents · hamel.dev evals FAQ].
- **LLM-as-judge:** binary pass/fail over 1–5 Likert; calibrate with TPR/TNR + Cohen's Kappa against a held-out human-labeled set (κ 0.4–0.6 substantial, ≥0.7 excellent — benchmarked against human-human agreement, often only 0.2–0.3); 100+ labeled examples plus ongoing weekly maintenance; swap argument order on pairwise comparisons to cancel position bias; give the judge an "Unknown" escape hatch; grade rubric dimensions separately; develop the judge with the most capable model first, cost-optimize later [documented: hamel.dev evals FAQ · eugeneyan.com/writing/product-evals/; research canon: EvalGen/SPADE, https://arxiv.org/abs/2404.12272].
- **Error analysis:** never outsource it; single "benevolent dictator" annotator by default; LLM assistance only after ~30–50 manual reviews, never for initial open coding. Custom lightweight annotation tooling reportedly ~10x faster than generic UIs. Agent-specific: transition failure matrix (last good state × first failure); annotate only the first upstream failure in multi-turn traces [documented: hamel.dev evals FAQ].
- **Human eval:** rubric with concrete anchors, frozen sample, ≥2 independent raters, measured inter-rater agreement, blind randomized presentation; κ < 0.4 means the rubric is broken, ≥ 0.8 means that dimension can be promoted to an LLM-judge. Thumbs-up/down product feedback tracks engagement, not quality — never a quality signal alone [documented: koji.so/docs/human-evaluation-ai-outputs · growthbook.io guide].
- **Prompt/model iteration:** the eval harness is wired into the config pipeline — any prompt/retrieval/model change auto-generates and auto-scores. Sample-size discipline: ~200 samples at ~3% defect rate → ±2.4% CI; margin halves only when samples quadruple. Prompt versioning with diffs and audit trail (LangSmith / W&B Weave / Braintrust-class tooling) [documented: eugeneyan.com/writing/product-evals/ · braintrust.dev docs].
- **Fine-tune vs prompt:** cost-ordered ladder — prompt engineering → RAG → fine-tuning → distillation; escalate only when the cheaper layer provably hits a wall [practitioner-consensus].
- **Model-upgrade regression:** every model swap re-runs the full regression suite against the last passing baseline — provider models update faster than release cycles and shift behavior under stable prompts [documented: futureagi.com/glossary/llm-regression-testing/].
- **Online experimentation:** pre-declared primary/secondary/guardrail metrics (no post-hoc metric shopping); guardrails enforced as constraints (hallucination, toxicity, PII, latency, cost); sequential testing for real-time violation detection; quantile treatment effects, not just averages; historical variance-based power calculations often fail after a model swap — metrics near raw model output shift variance dramatically [documented: growthbook.io guide · statsig.com/blog/what-are-guardrail-metrics-in-ab-tests].
- **Experiment readouts:** structured plan/readout — background, hypothesis, variants, metrics declared upfront, sample size, results, ship/hold/kill decision [practitioner-consensus].

### 2.4 The recurring cadence (synthesized checklist)

Daily: read a handful of fresh transcripts. Weekly: 10–20 outlier traces; triage new failures into the labeled set; check whether failing evals indict the grader or the system. Every 2–4 weeks: full error-analysis pass on 100+ fresh traces; refresh taxonomy, suite, and judge calibration. Every change: regression suite. Every experiment: written readout. On saturation: author harder tasks, don't celebrate the number.

## Part 3 — The platform environment (publicly documented)

What a new applied scientist in a large-company LLM copilot org can expect to encounter, from public documentation. Public-source strength varies sharply by area — the weakest-documented areas are exactly the biggest week-1 unlocks.

### 3.1 Online experimentation

- The employer runs a mature internal controlled-experiment platform ("ExP"): portal, execution service, log processing, analysis service; on the order of 100k A/B tests/year org-wide, with an extensibility framework letting orgs plug in custom analysis [documented: https://exp-platform.com/ · https://www.microsoft.com/en-us/research/publication/the-anatomy-of-a-large-scale-experimentation-platform/ · https://ieeexplore.ieee.org/document/11014941/].
- Expectation: model/prompt/feature changes ship through controlled flights with ring-based ramp, not direct deploys. [inferred]
- **Open question (not publicly documented):** how LLM response-quality metrics — as opposed to classic engagement metrics — are wired into the experiment analysis pipeline. The public ExP corpus predates the generative-AI era.

### 3.2 Copilot architecture (public docs)

- M365 Copilot is publicly described as an **orchestration layer**: user prompt → retrieval-augmented grounding via Microsoft Graph + the **Semantic Index** (tenant/user-level vector index, permission-trimmed — Copilot never surfaces content the user couldn't already access) → meta-prompt assembly (grounding + system/RAI directives) → LLM on Azure → post-processing and safety filters (prompt-injection, harmful-content, protected-material checks) [documented: https://learn.microsoft.com/en-us/microsoftsearch/semantic-index-for-copilot].
- Extensibility: declarative agents, API-plugin actions (incl. MCP servers), and Graph connectors in two models — synced (indexed) vs federated (live retrieval). A **developer mode** exposes which capability/action the orchestrator selected for a prompt — directly relevant to eval/debugging work [documented: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/ecosystem].
- Consequence for eval work: evals target one of several layers — retrieval/grounding quality, orchestrator routing/plan selection, response generation, safety filtering — and which layer the team owns decides what data and telemetry matter. [inferred]

### 3.3 ML/data platform

- Publicly documented only at the generic-Azure level: Azure Machine Learning (MLOps), Microsoft Fabric (analytics), the legacy Cosmos/SCOPE internal big-data stack [documented: https://vldb.org/pvldb/vol14/p3148-jindal.pdf], Kusto/ADX. What the copilot org actually uses day-to-day is **not public** and likely team-specific.
- This is the single biggest week-1 unlock: where eval sets and production telemetry live, and what the query tooling is (KQL? SCOPE? Spark?).

### 3.4 Dev tooling

- Microsoft is publicly migrating internal source control Azure Repos → GitHub, with the Copilot-adjacent org as pilot (~1,600 repos, 3,100+ devs in six months); Azure Boards (planning) and Azure Pipelines/1ES (CI/CD, build, compliance) remain in use alongside — a split model [documented: https://devblogs.microsoft.com/devops/azure-devops-and-github-journeying-into-the-ai-era/ · https://azure.microsoft.com/en-gb/solutions/devops/devops-at-microsoft/one-engineering-system/].
- **AI coding assistants — unsettled, verify on the ground:** third-party press reports that internal Claude Code access (opened Dec 2025) is being revoked in favor of GitHub Copilot CLI, with a June 2026 cutover deadline, starting in the Experiences + Devices division [reported: https://www.technobezz.com/news/microsoft-revokes-internal-claude-code-licenses-and-pushes-engineers-to-github-copilot · https://www.developer-tech.com/news/microsoft-claude-code-github-copilot-cli/]. Not confirmed by the employer publicly. **Working assumption for the unfold (A1): the sanctioned agent is most likely GitHub Copilot (CLI/Chat/Agent surfaces), not Claude Code** — the corpus's instructions-layer mapping must target that shape; verify day 1.

### 3.5 Responsible AI process

- The public **Responsible AI Standard v2** operationalizes six principles into goals → requirements → tools; product teams complete **RAI Impact Assessments** (public template), phased across release stages (private preview → public preview → GA), plus a stricter **Sensitive Uses review** for higher-risk cases [documented: https://blogs.microsoft.com/on-the-issues/2022/06/21/microsofts-framework-for-building-ai-systems-responsibly/ · https://www.microsoft.com/en-us/corporate-responsibility/responsible-ai-transparency-report/].
- Consequence: RAI review is a real ship-gate tied to the release calendar, not optional process. An applied scientist's eval work likely feeds these artifacts. [inferred]

### 3.6 Privacy/compliance posture

- Public commitments: customer prompts/responses/Graph data are **not used to train foundation models**; tenant isolation + encryption; permission-trimmed retrieval; EU Data Boundary honored (with a published carve-out: Anthropic models excluded from EUDB commitments); Purview sensitivity labels, retention, audit, and DLP all apply to Copilot interactions; web-grounding queries are a separate, identifier-stripped flow [documented: https://learn.microsoft.com/en-us/microsoft-365/copilot/enterprise-data-protection].
- Internal "eyes-off"/restricted-access data-handling practice for eval and telemetry datasets is **not publicly documented** — a must-ask, never assumed.

*Week-1 questions generated by every section above are consolidated in `week1-intake.md`.*
