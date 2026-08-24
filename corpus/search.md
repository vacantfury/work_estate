# Search — the estate's retrieval bus

*One retrieval seam over the job's many channels (design principle 25): mail, chat, calendar, docs and wikis, code and reviews, tickets, dashboards, the people directory, and whatever public search the environment sanctions. Every project queries through this seam; per-project hand-rolled channel access is a defect. Consumers: the communication flow's triage sweep, company-watch capture, the people harvest and silence checks, resources catalog discovery, worklog assembly, any project's research ask.*

## The service

- **One query seam.** "Find X" is asked once, against the bus; the bus fans out to the channels that can answer and returns cited results (source, link, date). Projects never each re-learn where things live: the placement map (`estate-structure.md`) covers the estate's OWN content, this bus covers the employer's surfaces.
- **The channel roster is resolved at unfold (A8):** which channels the sanctioned tooling can actually reach, each with its access mode — direct read seam · assisted read inside the tooling · user relay as last resort. The roster is a registry table; a channel gained or lost updates one row, never the consumers.
- **Read-only by default.** The bus retrieves; writes (sending, posting, filing) belong to their owning flows and gates (the communication flow's prepare-only rail).
- **Digs ride the bus:** scoped discovery campaigns (portable-skills `discovery-dig`) are the bus's campaign-sized form — brief and scoring meaning from the commissioning project, candidates typed into the store, a decided close.
- **Standing watches ride the bus:** company-watch capture, the people due lane's silence checks, resources window and catalog sweeps, and the triage sweep are all bus consumers on the engine's cadence — one adapter per channel serves them all.
- **Boundary:** employer surfaces plus whatever public retrieval the environment itself sanctions; no unsanctioned feed tooling (principle 12) and no channels beyond the job's own.

## Standing jobs (registry entries, `work-engine.md`)

- **Adapter roster upkeep** — re-check channel reachability whenever tooling or policy changes (a re-run trigger, Phase 1).
- **Watch dispatch** — run the standing watches through the roster on the engine's cadence.

## Fold-away note (for the unfold's A5 pass)

Core-adopt the SEAM rule at every outcome (consumers cite the bus, never channels); adapters land per A8. Degraded install: the bus is the one checklist of where to look.
