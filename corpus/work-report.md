# Work report — the role's twice-weekly steering loop

*A structured plan-vs-actual report on a fixed cadence (settled 2026-08-14): what the last range actually cost and produced, what the next range will cost and target. The user reviews each report and may return adjustments; the amended plan is the baseline the next report answers to. Two report days a week, at work end. The report is the role's steering instrument; the work record (`work-record.md`) is its raw material.*

## The three parts

1. **The time record** — real-time capture of actual working time, intervals included.
2. **The report** — generated at work end on each report day: last-range retrospective + next-range plan.
3. **The user's review** — they read each report and return a verdict and adjustments, which amend the next-range plan of record.

## The time record — `local/state/timelog.md`

Working time is RECORDED, never reconstructed — actual hours vary in both directions (overtime some days; an early stop when the work is done), so the report's time figures must be facts. Append-only timestamped lines, machine-local:

```
YYYY-MM-DD HH:MM start|stop|break|resume · <optional note>
```

- **Capture discipline:** a stamp is seconds of effort at a real moment — arrival, departure, lunch, a genuine interruption. Sessions stamp what they can observe (session open/close on a work task); the user stamps what only they know (arrival, meetings away from the machine, the day's end). Fine grain is not the point — honest day totals are.
- **Aggregation (computed at report time, never estimated):** focused time = start→stop minus breaks · interval/break time alongside it · overtime delta vs the standard day (the team's standard hours, discovered at intake — 8h default until resolved).
- **Day-1 fallback:** the format needs no tooling — a text file and a clock suffice from the first morning. Tooling (a stamp script, session hooks) may follow; the record never waits for it.

## The report — two report days a week, at work end

**Report days: Tuesday and Thursday (set 2026-08-14).** The week partitions into two ranges: Tue-end → Thu-end (Wed, Thu) and Thu-end → Tue-end (Fri, Mon, Tue). The asymmetry is deliberate: the range containing Friday — typically the lightest day in practice — is the longer one. The days are the user's call, never the unfold's; adapt only on their word.

Generated at work end on each report day into `local/state/reports/YYYY-MM-DD.md` by distilling the time record + the work record — a read, never a reconstruction ceremony. Template:

```
# Work report — YYYY-MM-DD (Tue|Thu)

## Last range: <prev report day> work-end → today (<workdays covered>)
- time: <h> focused · <h> intervals/breaks · overtime <±h> vs standard
- brain: low|med|high — <one line: what strained, if anything>
- did: <delivered/progressed items, one line each — from the work record>
- value: <what it earned — impact, growth, relationships, evidence>
- plan vs actual: <deltas from the last plan of record + why>

## Next range: today → <next report day> (<workdays>)
- planned time: <h> (vs <standard reference>)
- brain budget: low|med|high
- schedule: <the range's timed commitments — one line each: `Dow HH:MM–HH:MM <coarse label>`; "none known" if empty>
- targets: <one line each>
- intended value: <why these targets — what they should earn>
```

**The schedule line (settled 2026-08-14):** the next range's timed commitments — meetings, fixed blocks, events, known late days — read from the work calendar at report time, at record grain (time block + a coarse purpose label like "team sync" or "design review"; never confidential agenda content or attendee lists — the record grain rule, `boundary-protocol.md`). It exists for the user's conflict check against their commitments outside the job, which this installation cannot see; a collision comes back as a constraint to plan around. An empty range still reports "none known" — the absence of fixed commitments is itself information.

**The report is a record like any other:** the generating session writes it at the record grain (`boundary-protocol.md`) — the user's own effort-and-value accounting: hours, strain, what moved at meaning grain — never employer-confidential material.

## The user's review

The user reads each report and reviews it against everything this installation cannot see — their goals, health, calendar, commitments outside the job — and returns a verdict (approve, or refine with named changes), amendments to the next-range plan, and constraints to plan around. Ingest what they bring (in their own words, however they bring it), update the next-range plan of record, and use that amended plan as the baseline the NEXT report's "plan vs actual" line answers to. Never ask for more than they offer; if a report day passes with no word, the plan of record stands as generated.

## Consumers — why the loop pays

- **Steering:** plan-vs-actual at 2–3 day grain catches drift while it is cheap — scope creep, silent overtime, a target that keeps slipping.
- **Calibration:** recorded time against planned time teaches real task costs within weeks — estimates stop being guesses.
- **The user's leverage:** the review is the one standing moment their whole-life view steers the job's next range — without it, the job optimizes only locally.
- **Review-time evidence:** dated range reports with value lines are impact narratives already half-written (sharpening the `work-record.md` consumers).

## Fold-away note (for the unfold's A5 pass)

Core-adopt at every policy outcome — two local files and minutes per report day; the time record needs no tooling on day 1. Only the standard-hours reference adapts (intake); the report days are user-set and stand.
