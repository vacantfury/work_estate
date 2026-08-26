# skeleton/ — the estate's concrete form

The installed estate's default directory tree, shipped as real files. The corpus modules are the GENOMES (conventions, adaptive); this tree is the PHENOTYPE (structure, deterministic). The unfold **copies, then adapts — it never invents structure** (`UNFOLD.md` Phase 3): copy this tree to the A4 root, delete what A5 folds away, fill the ledger-resolved values, register everything in `hub/registry.yaml`. Where the two disagree, a module's convention text wins on MEANING and this tree wins on LAYOUT; a real conflict is a seed defect to report.

## The tree

```
<A4 root>/
  hub/           steward-mind: registry.yaml (the estate graph) · agent-jobs.yaml ·
                 self.md · decisions.md · failures.md · footprint.md · communication.md ·
                 _forms/ (lazy-founded kinds: lessons · handbook · campaign · playbook)
  store/         typed data + scoring service: schemas/schemas.yaml
  finder/        retrieval bus: sources.md (A8 knowledge roster)
  ties/          people-and-traffic bus: routing.md · drafts.md (no person stores — principle 29)
  worklog/       worklog.md · timelog.md · worklog-public.md (staging) · reports/
  compensation/  compensation.md (money-test register)
  career/        review.md · promotion.md · growth.md · themes.md · company.md (watch-job state)
  health/        health.md (floors tracker)
  risk/          risks.md (premortem register)
  research/      research.md (satellite registry; instantiated only where intake §18 clears it)
  main-work/     projects.md (portfolio board) · _template/ (per-project home: task surfaces + record.md)
  llm_utils/     ┐
  devices/       │ gated infrastructure: NOT copied at unfold — each dir is copied whole
  autoflow/      │ when its founding gate fires (see each INSTRUCTIONS.md)
  auto_research/ ┘
```

Every project also carries `INSTRUCTIONS.md` (scope + citations to hub law, never copies), `TODO.md` (`# TODO (ordered)`), `NOW.md`, and `archive.md`.

## Rules

- **Copy-then-adapt:** `_clone/` never copies (its `ledger.md` template seeds the seed clone's own gitignored `local/ledger.md`). The four gated dirs copy at their founding gates, not at unfold; `research/` copies only where intake §18 clears personal-stack presence. Everything else copies verbatim at unfold.
- **Template headers:** every file opens with a `skeleton template` comment naming its genome module; instantiation removes that line and adds the standard provenance header (`UNFOLD.md` §Update step 3). Update deltas diff installed files against these templates.
- **Legacy path resolution:** corpus references to `local/state/<file>` resolve to the owning project's directory in this tree via `hub/registry.yaml` (e.g. `local/state/worklog.md` → `worklog/worklog.md`). The registry is the resolver of record; this tree is its default answer.
- **Empty shells are still clutter:** `hub/_forms/` holds the FORMS of lazy-founded kinds (lessons, handbook, campaign, playbook); they are instantiated into a project only at that project's first entry, never pre-seeded.
- **Team practice wins:** the tree covers the estate's OWN records only. Where intake discovers a team surface for a content kind (status posts, design docs), that surface wins and the corresponding staging file retires (e.g. `worklog/worklog-public.md`).
