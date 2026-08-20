# Estate structure — shared conventions across the projects

*Estate-wide structural conventions every project shares (design principle 20d), ported selectively from the maintainer's broader working practice. Selection criterion: what makes an estate cumulative and self-correcting, carried as know-how only (principle 2: no machinery the seed cannot ship). Estate-wide law like the craft modules: consumed by every project, a project itself never.*

## The merged attention view (hub)

The hub can answer "what needs the user now" across the whole estate: one merged, ranked read over every project's TODO (due and active lanes) plus the standing due lanes (resources windows, connections threads, review cycles, health follow-ups). Rules:

- **Pull on ask, never push.** The view renders when the user asks; no per-project list auto-pops, no unsolicited digest.
- **The user's spoken priorities become pins.** When the user names something first or urgent, it pins above the computed order until done or unpinned; conversation is the one ordering channel.
- Convention first: a hub session computes the view by reading. An agent job may materialize it later; the job changes the labor, never the rules.

## Campaigns — the mid-scale ending form

Work larger than a task but smaller than a standing project (an org-networking push, an enrollment arc, a promotion push) runs as a **campaign**: one folder in the owning project, with `campaign.md` as the state file carrying a NAMED end, a small roster (pointers to cards/entries, never copies), an append-only move log, and exit criteria. The container never competes for attention; its individual moves ride the ordinary TODO. A campaign ends by DECISION: the closing pass records outcome against the named end plus lessons, and puts extend/close to the user explicitly. A silent lapse is a defect.

## Lessons and handbook — lazy-founded, per project

- **`lessons.md`** — founded at a project's first lesson: concrete incidents worth keeping, each as story · mechanism · the rule that prevents recurrence.
- **`handbook.md`** — founded at a project's first point: established practice points (the correct way, the wrong way, the better way), each with where it was learned.

Estate-wide items land in the hub's copies. These files are why the estate improves instead of re-deriving; a lesson that stays in a session transcript is a lesson lost.

## The failures log and the self-audit

- **One estate failures log** (hub, `local/state/failures.md`): a dated row per real failure — what happened · cause side (system / instruction gap / process / tooling) · coarse severity. A person's error under absent or incomplete instruction attributes to the system, never the person (`session-discipline.md` completeness rule).
- **A periodic self-audit job** (engine registry): sweep the log and the estate for recurring causes, stale boards, and conventions nobody follows; propose the highest-value fixes as one batch, weighted by cost of recurrence, never by raw counts. Fixes that change behavior wait for the user's word; mechanical fixes apply.

## The data-shape rule

Any register that scores or types its entries (people cards, the resources register, the company watch) follows one shape:

1. **Typed entries** with named fields, not free prose.
2. **Append-only dated assessments** carrying their evidence; corrections are new lines, never edits of old ones.
3. **Machine estimates separate from the user's own judgments** — labeled, and the user's layer never overwritten.
4. **Weights, thresholds, and cadences in a config block**, tunable, never buried in prose or code.

Markdown registers are fine at estate scale; the shape matters, not the storage engine. If a register ever outgrows markdown, the shape migrates unchanged into whatever store the sanctioned tooling offers.

## What is deliberately NOT ported

Heavier structure from the maintainer's practice stays out until a real work-side consumer exists: no standing multi-agent deliberation INFRASTRUCTURE (the deliberation convention itself is in — `deliberation.md`, know-how run inside the sanctioned tooling), no version-tagged releases (the estate ships no software), no databases or schedulers beyond what the sanctioned tooling provides, no external-feed collection (design principle 12).

## Fold-away note (for the unfold's A5 pass)

Core-adopt: each convention costs at most a file. On a degraded (no-agent) install, the attention view and self-audit become session-opening reads; everything else is unchanged.
