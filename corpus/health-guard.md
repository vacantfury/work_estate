# Health guard — hard floors for work, and the work/personal wall

*The standing ordering (settled 2026-08-13): health ranks above personal life, and both rank far above work — work never buys anything with health. This module is a FLOOR, not a target: the operating posture's delivery targets (design principles 7 and 9) optimize strictly inside it. It binds the user's own working behavior and every session working beside them, in the office and at home alike.*

## The hard floors (non-negotiable defaults)

1. **Sleep** — no deadline, launch, or review cycle buys sleep. Late work never extends into the sleep window; the task waits for tomorrow.
2. **Meals** — real meals, at real times, away from the desk. A meeting does not delete lunch; it moves it.
3. **The hard stop** — the workday ends at a set time (chosen with the user at intake, recorded in `local/`). Past it, work happens only as a named exception (breach log below) — never as drift.
4. **Movement and eyes** — the in-day cadence in the moment table.
5. **Symptoms outrank commitments** — pain, repeated poor sleep, persistent strain: the schedule bends, not the body. The session helps renegotiate the commitment (the prioritization idiom, `project-lifecycle.md`), never helps push through.

## Moment instructions — what to do, exactly, when

The user never has to remember or translate these; the guard tells them at the moment. Defaults below; cadences and times are calibrated with the user at intake and recorded in the ledger.

| Moment | Do exactly this |
|---|---|
| ~60 min continuous sitting / screen work | Stand up. Move 2–5 min (water run, corridor loop). While up, look at something far away for ~20 s. Then continue. |
| ~2 h of deep work done | Longer break, ~10 min: leave the desk — daylight, stairs, or a walking loop per the facility map. |
| Eye strain felt (or every ~20 min of hard screen focus) | 20-20-20: look ~20 ft (6 m) away for 20 s. Cheap — do it liberally. |
| Lunch window opens | Real meal, away from the desk (cafeteria/kitchen per the facility map). The block lives on the calendar; meetings move around it. |
| Hard-stop time reached | Close the work laptop. Anything unfinished becomes one TODO line, not one more hour. Continuing anyway = declare the exception and log it. |
| On-call page arrives off-hours | Handle it — on-call is duty, not a breach (wall section below). Log it as an on-call event so real load stays visible. |
| A symptom appears (pain, strain, a bad-sleep streak) | Stop the current push. Tell the session: it renegotiates the commitment and points at the concrete facility fix (equipment request, ergonomics program, medical resource per the facility map). |

## Grounding rule — facility docs first, or ask (binding)

No concrete practice in this guard is ever invented from assumption. Before any instruction binds to a facility (gym, cafeteria, sit-stand desk, ergonomics program, break spaces, on-call tooling), the session FIRST checks the employer's facility/benefits documentation — and where the docs don't answer, asks the user — then records the resolved facility map in `local/`. Intake §14 (`knowledge/week1-intake.md`) is the first full pass; re-ground on office moves or policy changes.

## Facilities the guard runs on

- **Office:** ergonomic setup in week 1 — chair adjusted, monitor at eye height, external keyboard/mouse (never laptop-hunched); sit-stand desk availability; the ergonomic-equipment request channel (request early, at eligibility — never wait for pain); gym/fitness access; cafeteria locations and hours; walking routes for breaks and walking 1:1s.
- **Home (WFH days):** the same ergonomic bar — real desk, real chair, external monitor — and ONE dedicated work spot, which is also the wall's physical mechanism: work happens there, and leaving it ends the workday. Employer-provision-first (settled 2026-08-14): the employer's home-equipment provision/reimbursement channel is checked BEFORE any personal purchase — the station is furnished through it; personally bought only what it doesn't cover.
- **The guard's clock:** the moment table needs a trigger. The unfold wires the best mechanism the device and sanctioned tooling actually offer — calendar blocks, OS or assistant break reminders, the sanctioned agent's own reminder surface; degraded path: recurring timers on the user's own phone plus the printed moment table.

## The tracker — `local/state/health.md`, on the work machine

Record posture (settled 2026-08-13, generalizing the company-watch record ruling): the tracker lives ON the work device, candid and complete, kept for the user's benefit — workday health behavior is the user's own information, conflicts with nothing, and is never thinned for appearance; conservatism about the user's own content on the work device applies only on REAL risk or real company conflict, never by default. Format (unfold-seeded):

```
# Health tracker (work) — floors + breach log

## Daily line (append; one line a day is enough)
- YYYY-MM-DD · stop kept? · breaks ~n · lunch real? · on-call events · strain notes

## Breach / exception log (append-only)
- YYYY-MM-DD · which floor · named exception or drift · why · repaid how
```

Sessions append what they observe; the user adds what only they know (sleep, symptoms). **Enforcement:** a session that sees work running past a floor names it at that moment — one neutral line — and records it. A floor is crossed only by the user's explicit named exception; anything else is logged as drift. Repeated breaches (2+ in a week) become a standing finding in the weekly debrief (`work-record.md`), so the user sees the pattern and can intervene.

## The wall — separating work from personal life (with the on-call carve-out)

Isolate everything that CAN be isolated; on-call duty flows through.

- **Default-closed:** no work accounts on personal devices — no work mail, Teams, or chat on the personal phone, so after-hours work cannot page. Closing the work laptop ends the workday. At home, work happens only at the dedicated spot. The calendar protects the evening past the hard stop by default.
- **The on-call carve-out (settled 2026-08-13):** when the role carries an on-call rotation, the channel the rotation genuinely requires stays open for its window — scoped to exactly that channel and window, per the team's real practice (intake §14 discovers the rotation's true shape). On-call responses are never breaches; they are logged as on-call events so real load stays visible. Everything outside the required channel and window stays behind the wall even during on-call.
- **Team-reality check:** reachability expectations are discovered, never assumed (intake §10/§14). If the team genuinely expects some after-hours channel beyond on-call, that becomes ONE deliberate, minimal, user-chosen exception recorded in the ledger — never silent drift toward always-reachable.

## Debrief line

The weekly debrief carries a `health:` line (format home: `work-record.md`), so the user's lifelong health picture accumulates across jobs — the working tracker itself stays on this machine.

## Fold-away note (for the unfold's A5 pass)

Core-adopt at every policy outcome — the guard costs one local file, a few calendar blocks, and session attention. Only the clock wiring varies by A1; the degraded path runs on phone timers and the printed moment table.
