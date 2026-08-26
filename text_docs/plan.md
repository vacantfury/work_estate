# work_estate — plan

```yaml
state: active
last_settled: 2026-08-26
running: v6.0.0        # latest shipped seed tag; the version an installed estate updates against
re_plan_triggers:      # settle events only, never cadence
  - a seed install or update surfaces a structural gap (missing template, underdetermined layout)
  - the maintainer's upstream working practice settles a change that crosses the porting bar
  - employer policy or tooling shift forces an unfold contract change (A1–A8 semantics)
```

## Arc

The seed reached install grade v1.0.0 (2026-08-24, first install complete) and has since hardened structure: the v2–v3 clear-structure restructures (roster by content kind, infrastructure at end-state), the v4–v5 single-person-home corrections, and v6 shipping the concrete skeleton (structure as phenotype: copy-then-adapt install, template-diff updates). The repo is a shipped, versioned installer in maintenance-and-refinement: content evolves by settle-time ports from the maintainer's practice (axis 1) and by gaps the installed estate's real use surfaces (reported through the user, never through the repo).

## Milestones

- **v6.0.0 — the concrete skeleton** *(shipped 2026-08-26)*: `skeleton/` template tree, UNFOLD Phase 3 copy-then-adapt, project-module seam re-cut, one-line corpus index.
- **Next (unscheduled, consumer-driven):** installed-estate conformance pass at the work clone's next update pull — skeleton adoption, missing-file fill, ledger re-check. Rides the user's update run, not a seed change.

## Risks (premortem; predictive lane)

- **Installed estate diverges structurally from the skeleton** — early signal: update pulls repeatedly report "edited since generation" merges on structural files · reaction: conformance report at the update check step, user decides adopt-vs-keep per file; living state never moved without the user's word.
- **Update channel goes dark (A2 policy shift)** — early signal: fetch fails at the check step · reaction: seed continues to serve in reading form; re-run detect at the next policy change; the clone remains deletable without loss.
- **Corpus outgrows one-file-per-convention legibility again** — early signal: the index or a module needs re-explaining in sittings · reaction: the estate-structure law-layer form (record-per-rule + generated view) is the named successor; adopt at that settle, not before.

Tasks live in `TODO.md` (gitignored); this plan only points. Design record: `text_docs/design.md`. Update manifest: `CHANGELOG.md`.
