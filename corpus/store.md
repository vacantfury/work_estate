# Store — the estate's typed data service

*One shared typed store + scoring service that every register rides (design principle 25). The data-shape rule (`estate-structure.md`) is this service's CONTRACT; this module is the ENGINE that enforces it. Consumers: the people cards, the resources register, the company signal and theme registers, the worklog's structured lines, per-project boards — any register that types or scores its entries.*

## The service

- **One store, many entity kinds.** Each kind (person, thread, resource, event, theme, signal, work item, decision, failure row) declares a SCHEMA: named fields, and which fields are machine-computed versus the user's own judgment. Schemas live in one config home under the store; registers never invent ad-hoc shapes.
- **Scoring runs in the store; meaning stays with the owning project.** A register's scoring config (weights, thresholds, bands — the data-shape rule's config block) is authored by the owning project; the store executes it uniformly and stamps every score with config version, date, and an evidence pointer.
- **Append-only assessments; the user's judgment layer is never overwritten** (data-shape rule points 2–3).
- **Views, not copies.** Once the store runs, the markdown files sessions read (`people.md`, `resources.md`, …) are RENDERED views; a hand edit to a view that carries judgment flows back as a new user-layer line, never silent divergence.
- **The engine is resolved at unfold (A7):** the best sanctioned storage engine the device offers — an embedded database where a runtime exists (SQLite-class), the tooling's native memory otherwise. Markdown-with-shape is the bootstrap form; migration is the data-shape rule's own line: the shape moves unchanged, the store owns the move.

## Standing jobs (registry entries, `work-engine.md`)

- **Schema keeper** — a new entity kind lands as a schema entry first; drift between a register and its schema is flagged, never silently absorbed.
- **Scoring runs** — recompute machine scores on the owning project's cadence; a delta surfaces through the hub attention view only when it changes a decision lane.
- **Store health** — backup per A6; row counts and staleness read at the self-audit.

## Fold-away note (for the unfold's A5 pass)

Core-adopt the CONTRACT at every outcome (the data-shape rule already binds); the ENGINE lands when A7 finds a sanctioned store. Degraded install: markdown registers keep the shape, scoring is a session pass.
