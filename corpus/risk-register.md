# Risk register — predict and plan for failure

Failure management has two halves: reacting well when something breaks, and — the half this module owns — predicting the likely failure modes and holding a pre-planned reaction before anything breaks. At work the predictive half carries most of the weight: stakes are higher, feedback loops are slower, and the costly failures (a ramp that falls behind, a demo that breaks live, a priority misread) are largely anticipatable. Prediction beats reaction wherever the first occurrence is unaffordable.

## The register — standing state

- One work-local register (the unfold seeds `local/state/risks.md`) holds every live risk, one entry each:
  - **failure mode** — one line, concrete;
  - **early-warning signal** — what would be observable before it lands, and where it would show (a 1:1, CI, a review thread);
  - coarse **likelihood × impact** bands (low/med/high × minor/major/critical — bands, never precise numbers; false precision is its own failure mode);
  - **reaction plan** — the pre-decided first moves when the signal fires, including who hears about it and how early;
  - optional **escalation trigger** — the condition that turns the reaction from quiet fix into raised flag.
- The record is candid and complete (design principles 12/13): the register exists to be useful, so it names real risks at full grain — including the uncomfortable ones (behind schedule, expectations misread). A sanitized register protects appearances and nothing else.
- Review rides existing rhythms, never a new ceremony: the portfolio review (`project-pipeline.md`) re-reads the register; signals are checked where they would naturally be visible; entries retire explicitly when their window closes (a risk that can no longer happen is deleted with a line, not left to rot).

## Premortems — where entries are born

- **Per project, at accept:** before work starts, one short pass — "it is three months later and this project failed: why?" The top answers become register entries with reactions. The natural twin of the landing declaration (`project-pipeline.md` stage 8): accept time declares both what done looks like and how it most plausibly dies.
- **Per transition:** big shifts (onboarding, a new charter, a reorg, a new manager) get their own premortem — the ramp seed below is the first instance.
- An entry without a reaction plan is not an entry — the plan is the point; likelihood guesses alone change nothing.

## Reaction plans — the discipline

- Written when calm, executed when not: each plan names the first concrete moves, the communication step, and what NOT to do (no silent heroics past the escalation trigger).
- Early honesty is the near-universal reaction component: for almost every work risk the cheapest reaction includes surfacing it to the manager before it becomes visible on its own — a raised flag with a plan builds credibility, a discovered slip spends it (the status-honest-and-early norm, `project-pipeline.md` stage 6, applied at its highest-value moment).

## Calibration — score the predictions

When something does fail, check the register before closing the incident: **predicted-and-plan-worked** (the system paid for itself) · **predicted-but-plan-failed** (fix the plan, not just the incident) · **unpredicted** (add the entry now, while the shape is fresh). Reviewing the hit-rate at natural retrospectives keeps prediction an honest, improving practice instead of a ceremony.

## Seed premortem — the first 90 days (new-role ramp)

The unfold carries these into `local/state/risks.md` as the register's opening entries, adapted to what intake discovers; they are generic new-role failure modes, deliberately unspecialized.

- **Ramp falls behind the expectations bar** — signal: 1:1s stay vague on whether progress is "on track"; no committed early deliverable · med × critical · reaction: ask the manager directly for explicit 30/60/90 expectations and a named first deliverable; re-anchor against them weekly.
- **Expectations misread (working hard on the wrong thing)** — signal: feedback tone diverges from self-assessment; assigned work drifts from what the org visibly values · med × major · reaction: re-derive priorities from the manager's own words at the next 1:1; restate what "good" looks like and get it confirmed.
- **First visible artifact breaks (demo, readout)** — signal: no rehearsal on the real environment; dependencies untested · med × major · reaction: dry-run on the real surface at least a day early; hold a degraded fallback (slides, recording) ready; if it still breaks live, narrate the fallback calmly — visible recovery is itself legible competence.
- **Blocked on access/permissions/environment** — signal: setup items still open after the first days · high × minor · reaction: escalate early through the onboarding buddy/manager with a specific itemized list — access friction is expected to be raised, not endured.
- **Overcommitment in the eagerness window** — signal: saying yes faster than the review cycle can absorb the output · med × major · reaction: route every new ask through the prioritization frame (`project-pipeline.md` stage 4) from day one.
- **Relationship building deferred under delivery pressure** — signal: weeks pass with no conversations beyond required ceremonies · med × major · reaction: book the intro-1:1 rhythm in week one (peers, adjacent teams) and treat it as delivery, not overhead.
