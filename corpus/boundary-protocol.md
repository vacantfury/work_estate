# Boundary discipline — what belongs where

*The standing rules for what lives inside the employer boundary and what belongs to the owner's own estate. Simple in daily use: employer material stays in employer systems; the owner's own records are written at meaning grain.*

## Premise: this installation is self-contained

The installation runs on the work account, work surfaces, and the work budget only. The rules:

- **Employer-confidential content stays in employer systems.** It never enters the owner's own repos, sidework, or any non-employer channel (the owner's IP rule, and employer policy). Gray flows are decided by work policy discovered at intake — default no before the check.
- **The owner's own estate on this machine is accepted and, where it benefits him, deliberate.** Incidental logins (Gmail, a browser profile, ordinary browsing) are his normal life, never engineered around. Deliberate presence — his secret manager, his LLM seam library with his own keys, clones of his own research repos, access to his own compute — is allowed and governed by `research-infrastructure.md` (what and how) and `device-return.md` (revocable per-device entry, footprint register, clean exit). Work-side agents and jobs still default to work surfaces only and never reach into his logins.
- **Hard core, three lines:** employer-confidential content never leaves employer systems through the owner's own channels · the owner's hub and dossier content never lands on this machine · the work engine's standing jobs run on work surfaces and the work account's budget only.
- **Git traffic on the owner's own repos** (pull/push of his own research engines) is his own estate's ordinary versioning happening through this device. The one-way rule binds it: nothing work-derived is ever committed into his own repos.

## The record grain rule

Every record the owner keeps on this machine — the worklog, reports, the weekly debrief, jottings, sidework — is written at **meaning grain**: his own effort-and-value accounting. How the role is going, what he is learning, workload and strain, time figures, career-relevant events, people at relationship grain. **Never employer-confidential material:** no internal code, data, documents, unreleased product information, confidential agenda content, or attendee lists. When in doubt, leave it out — the meaning matters, not the material.

Because every record is born at this grain, whatever the owner later does with his own records is safe by construction — no filtering step exists or is needed. The session writing a record enforces the grain; the owner never polices it.

## Division of subject matter

- **This installation: the job.** Day-to-day work management — tasks, sessions, records, conventions — inside the employer boundary.
- **The owner's wider planning** (career strategy, long-term growth, everything beyond the job) is his own affair, handled elsewhere. When he brings a posture or convention update, ingest what he states into `local/` notes and conventions — never ask for more than he offers.

Nothing is homed in two places.

## Seed refresh

`git pull` + re-run the unfold, when the owner initiates it — conventions only. Credential-free by design: this repo is public (owner decision 2026-08-06), so clone and pull need no authentication under any policy that allows reading public GitHub.

## Credential rule (amended 2026-08-15)

The owner's own credentials on the work device are ALLOWED (owner ruling 2026-08-15, superseding the 2026-08-06 never-sign-in rule): they enter in the most revocable per-device form — fine-grained per-device tokens or SSH keys scoped to the repos actually needed, device-scoped secret-manager authorization — with every landing logged in the footprint register at that moment (`device-return.md`) and the highest-tail-risk credential classes excluded from the device. Setup order and scope: `research-infrastructure.md`. Account passwords and broad classic tokens remain never-store.

## Fold-away note (for the unfold's A5 pass)

Core-adopt at every policy outcome: these are content-placement rules, costing nothing to hold. Only the seed-refresh line depends on A2; if the remote is unreachable, strike it and the rest stands unchanged.
