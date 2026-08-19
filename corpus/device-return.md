# Device return — the uninstaller

*The graded boundary (design principle 17) is safe only when paired with a clean exit: personal presence on the work machine is allowed BECAUSE it can be fully and provably withdrawn. This module is the standing exit machinery — the mirror of `UNFOLD.md`. Settled 2026-08-15: return-device preparation is a real multi-operation procedure — prepared continuously, never reconstructed at the exit.*

## The footprint register — `local/state/footprint.md`

The register that turns exit into a checklist read instead of archaeology. **Binding rule: nothing personal lands on this machine without a register line written at the moment it lands, and every entry's revocation path is known at entry** — revocability-first: the most revocable per-device form is chosen precisely so that the exit line is one operation.

Line format:

```
YYYY-MM-DD · <what landed> · <kind: sign-in | credential | clone | tool | data> · <issuer-side revocation: where + what to revoke> · <local removal: what to delete>
```

Seeded by the unfold. Audited whenever this module runs: a personal item found on the machine with no line is a defect — add the line, then fix the intake habit. **Register deltas land in the weekly debrief** (employer-safe by nature: "per-device credential issued for <service>"), so the user always holds a near-current mirror of the register off this machine — this is what makes the loss variant below executable.

## Triggers

The full procedure fires on ANY of: offboarding / device return · device replacement or reimage · repair hand-in (temporary loss of custody) · device loss or theft (remote variant below) · a policy change ending personal presence on the device.

## The procedure

Order matters: **revoke at the issuer first, delete locally second** — local deletion without issuer-side revocation leaves live credentials in backups, caches, and employer disk images.

1. **Walk the register, issuer side:** for every credential and sign-in — revoke the per-device token/key at the hosting service, deauthorize this device in the secret manager, sign out AND remove browser profiles (clearing synced data on the device), revoke cluster access credentials. Verify at each issuer: its device/session/key list no longer shows this machine.
2. **Walk the register, local side:** delete personal repo clones, the seam library, `local/`, personal tool state, caches and shell-history entries holding personal paths or tokens.
3. **Work-owned content:** handled by the employer's own offboarding process — handed back, never carried out. The one-way rule holds to the last day.
4. **Final sweep:** search the home directory for leftovers beyond what the register listed — key files, tokens, clones, `.env`-class files.
5. **Close the loop:** one line in the user's own records noting the device retired and the register fully executed, so the exit is on record off this machine.

Repair hand-in runs the same procedure (re-installation afterwards is cheap: re-run the setup order in `research-infrastructure.md` plus the unfold); for a short, low-risk repair the user may explicitly scope it down to step 1 — their call, logged.

## Loss/theft variant

No custody, so only the issuer side exists: run step 1 immediately FROM ANOTHER OF THE USER'S DEVICES, using the debrief-carried register mirror plus each issuer's own device/key list (which is authoritative and enumerable from any logged-in personal device). Then report the loss through the employer's process for the device itself.

## Fold-away note

Core-adopt the moment ANY personal item lands on the machine; the unfold seeds the register either way (an empty register is simply a trivially-clean exit).
