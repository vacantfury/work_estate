# Compensation — pay and the money-valued claims

*The money project (design principles 20a + 28). Everything the employer gives the role that is money or directly priceable in money is managed here as ONE portfolio: pay itself, benefit elections, budgets, quotas and access. Most of its value is lost by not knowing, not electing, or missing a window. This project manages the portfolio the way an asset manager manages accounts: know the catalog, elect deliberately, never miss a window. Operating law: **acquire normally-accessible resources at eligibility, not at need.** A resource claimed when it becomes available is cheap; the same resource chased when suddenly needed is expensive or gone.*

## Scope: the money test, four kinds

A thing belongs here iff it is money or directly priceable in money. Four kinds:

- **Pay** — base salary, bonus target and outcomes, stock awards and their vest schedule, sign-on terms, merit/raise mechanics. Each component is a register entry (its mechanics and calendar); pay-affecting cycles — merit and bonus cycles, vest dates, refresh windows — ride the due lane like any claim window. The promotion CASE lives in `career.md`; the pay outcome and its mechanics land here.
- **Benefit elections** — retirement plan and employer-match mechanics (including after-tax conversion paths where offered), stock purchase plans, health savings accounts, insurance elections, wellness and perk allowances. The kind with hard windows: enrollment periods close, and a closed window usually stays closed until the next cycle.
- **Budgets** — learning/training budget, conference budget, equipment and home-office allowances: claimable amounts that typically expire each cycle. An expired unclaimed budget is value burned.
- **Access** — compute quotas, license seats, data and tool access the role can request: usually free to claim, each carrying a direct dollar price all the same.

Career-development opportunities — programs, mentorship, internal speaking, hackathons, trainings, growth events — fail the money test (no direct price) and live in `career.md` §Growth (split settled 2026-08-24; the scope test settled 2026-08-25). The window machinery here applies to register entries only.

## The register — `local/state/compensation.md`

One entry per pay component or claimable resource: what it is · eligibility (who, from when) · window (enrollment/claim deadlines, cycle resets, vest dates) · state (unexamined / elected: which choice / claimed / declined: why / not yet eligible `[after:]`) · value note (what it is worth to the user, one line). Every window lands as a dated `[due:]` line in the project TODO with the standard two-day buffer (`task-convention.md`). Record posture: candid and complete; pay components, election states, and windows are meaning grain (`boundary-protocol.md`).

## Standing jobs (registry entries, `work-engine.md`)

- **Catalog discovery** — walk the employer's compensation/benefits/perks portals and internal program indexes at install (intake §19) and at each cycle boundary; append what is found. The pay components seed from the offer packet at install. The catalog is discovered, never assumed: the failure mode this project exists against is the resource nobody told the user about.
- **Window watch** — the due lane: surface every election, claim, or pay-cycle window opening or approaching. At a fresh employment the FIRST act is reading the new-hire enrollment window off the enrollment portal: such windows are short, and missing one is usually irreversible until the next cycle.
- **Election preparation** — for each due election: the options, one recommendation with its one-line why, the do-nothing consequence, and the execute-ready package (`human-agent-collaboration.md` choice-surface form). **Submitting an election is always the user's press.**

## The boundary split

This project owns pay structure, discovery, eligibility, windows, elections, and execution mechanics. The resulting HOLDINGS (account balances, vested equity, insurance in force) and their financial meaning are the user's own affair beyond this installation; facts cross by the user's own word. No account values, portfolio math, or financial planning live on this machine: the register needs to know what the pay components are and that an election was made, never what the accounts are worth.

The register rides the store service (`store.md`); catalog discovery and window watching query through the finder (`finder.md`).

## Fold-away note (for the unfold's A5 pass)

Core-adopt at every policy outcome: one register plus a due lane. The standing jobs degrade to a session-opening checklist where no agent runtime exists.
