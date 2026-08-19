# Boundary discipline — what belongs where

*The standing rules for what lives inside the employer boundary and what belongs to the user's own estate. Simple in daily use: employer material stays in employer systems; the user's own records are written at meaning grain.*

## Premise: this installation is self-contained

The installation runs on the work account, work surfaces, and the work budget only. The rules:

- **Employer-confidential content stays in employer systems.** It never enters the user's own repos, sidework, or any non-employer channel (the standing IP rule, and employer policy). Gray flows are decided by work policy discovered at intake — default no before the check.
- **The user's own estate on this machine is accepted and, where it benefits them, deliberate.** Incidental logins (a personal mail account, a browser profile, ordinary browsing) are normal life, never engineered around. Deliberate presence — the user's secret manager, their LLM seam library with their own keys, clones of their own research repos, access to their own compute — is allowed and governed by `research-infrastructure.md` (what and how) and `device-return.md` (revocable per-device entry, footprint register, clean exit). Work-side agents and jobs still default to work surfaces only and never reach into the user's logins.
- **Hard core, three lines:** employer-confidential content never leaves employer systems through the user's own channels · the user keeps their private life-records off this machine · the work engine's standing jobs run on work surfaces and the work account's budget only.
- **Git traffic on the user's own repos** (pull/push of their own research engines) is their own estate's ordinary versioning happening through this device. The one-way rule binds it: nothing work-derived is ever committed into the user's own repos.

## The record grain rule

Every record the user keeps on this machine — the worklog, reports, the weekly debrief, jottings, sidework — is written at **meaning grain**: their own effort-and-value accounting. How the role is going, what they are learning, workload and strain, time figures, career-relevant events, people at relationship grain. **Never employer-confidential material:** no internal code, data, documents, unreleased product information, confidential agenda content, or attendee lists. When in doubt, leave it out — the meaning matters, not the material.

Because every record is born at this grain, whatever the user later does with their own records is safe by construction — no filtering step exists or is needed. The session writing a record enforces the grain; the user never polices it.

## Division of subject matter

- **This installation: the job.** Day-to-day work management — tasks, sessions, records, conventions — inside the employer boundary.
- **The user's wider planning** (career strategy, long-term growth, everything beyond the job) is their own affair, handled elsewhere. When they bring a posture or convention update, ingest what they state into `local/` notes and conventions — never ask for more than they offer.

Nothing is homed in two places.

## Seed refresh

`git pull` + re-run the unfold, when the user initiates it — conventions only. Credential-free by design: this repo is public (decided 2026-08-06), so clone and pull need no authentication under any policy that allows reading public GitHub.

## Credential rule (amended 2026-08-15)

The user's own credentials on the work device are ALLOWED (settled 2026-08-15, superseding the 2026-08-06 never-sign-in rule): they enter in the most revocable per-device form — fine-grained per-device tokens or SSH keys scoped to the repos actually needed, device-scoped secret-manager authorization — with every landing logged in the footprint register at that moment (`device-return.md`) and the highest-tail-risk credential classes excluded from the device. Setup order and scope: `research-infrastructure.md`. Account passwords and broad classic tokens remain never-store.

## Fold-away note (for the unfold's A5 pass)

Core-adopt at every policy outcome: these are content-placement rules, costing nothing to hold. Only the seed-refresh line depends on A2; if the remote is unreachable, strike it and the rest stands unchanged.
