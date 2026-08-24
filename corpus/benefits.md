# Benefits — the money-like claims

*The internal-assets project (design principle 20a). An employer grants a role a whole portfolio of resources: benefit elections, budgets, programs, quotas, tool and data access. Most of its value is lost by not knowing, not electing, or missing a window. This project manages that portfolio the way an asset manager manages accounts: know the catalog, elect deliberately, never miss a window. Operating law: **acquire normally-accessible resources at eligibility, not at need.** A resource claimed when it becomes available is cheap; the same resource chased when suddenly needed is expensive or gone.*

## Scope: three claim kinds

- **Benefit elections** — retirement plan and employer-match mechanics (including after-tax conversion paths where offered), stock purchase plans, health savings accounts, insurance elections, wellness and perk allowances. The kind with hard windows: enrollment periods close, and a closed window usually stays closed until the next cycle.
- **Budgets** — learning/training budget, conference budget, equipment and home-office allowances: claimable amounts that typically expire each cycle. An expired unclaimed budget is value burned.
- **Access** — compute quotas, license seats, data and tool access the role can request: capability-bearing, usually free to claim.

Career-development opportunities — programs, mentorship, internal speaking, hackathons, trainings, growth events — are NOT claims and live in `career.md` §Growth (split settled 2026-08-24: money-like versus development). The window machinery here applies to claims only.

## The register — `local/state/benefits.md`

One entry per resource: what it is · eligibility (who, from when) · window (enrollment/claim deadlines, cycle resets) · state (unexamined / elected: which choice / claimed / declined: why / not yet eligible `[after:]`) · value note (what it is worth to the user, one line). Every window lands as a dated `[due:]` line in the project TODO with the standard two-day buffer (`task-convention.md`). Record posture: candid and complete; election states and windows are meaning grain (`boundary-protocol.md`).

## Standing jobs (registry entries, `work-engine.md`)

- **Catalog discovery** — walk the employer's benefits/perks portals and internal program indexes at install (intake §19) and at each cycle boundary; append what is found. The catalog is discovered, never assumed: the failure mode this project exists against is the resource nobody told the user about.
- **Window watch** — the due lane: surface every election or claim window opening or approaching. At a fresh employment the FIRST act is reading the new-hire enrollment window off the enrollment portal: such windows are short, and missing one is usually irreversible until the next cycle.
- **Election preparation** — for each due election: the options, one recommendation with its one-line why, the do-nothing consequence, and the execute-ready package (`human-agent-collaboration.md` choice-surface form). **Submitting an election is always the user's press.**

## The boundary split

This project owns discovery, eligibility, windows, elections, and execution mechanics. The resulting HOLDINGS (account balances, vested equity, insurance in force) and their financial meaning are the user's own affair beyond this installation; facts cross by the user's own word. No account values, portfolio math, or financial planning live on this machine: the register needs to know that an election was made and what it was, never what the account is worth.

The register rides the store service (`store.md`); catalog discovery and window watching query through the finder (`finder.md`).

## Fold-away note (for the unfold's A5 pass)

Core-adopt at every policy outcome: one register plus a due lane. The standing jobs degrade to a session-opening checklist where no agent runtime exists.
