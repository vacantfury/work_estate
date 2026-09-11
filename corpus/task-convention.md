# Task convention (portable)

One tree for the user's work, with an ordered TODO as its attention surface. The store-backed form is standard where an engine exists; markdown keeps the same model as a tooling-agnostic bootstrap or degraded form.

## The work tree

Everything the user does is a node in ONE tree. Leaves are tasks; containers coordinate work or provide its project home. Six kinds come from scope and lifetime (work-node kinds; the project registry's `kind` field in `estate-structure.md` is a separate axis):

| Scope | Finishes | Keeps running |
|---|---|---|
| Single action | task | recurring task |
| Coordinated effort | campaign | playbook |
| Project home | project with a named end | standing project |

The stored kinds for the last two cells are `bet` and `organ`, respectively; the seed calls both **projects**. Kind is stored, lifetime follows from it, and duration is never a kind. A recurring task is plain repetition with separately completable task occurrences. A playbook is conditional work with remembered state and the founding bar in `estate-structure.md`.

- **One home and at most one parent per node.** The home is the project where the work belongs, with its registered path; only a container can parent work. When the work changes locus, transfer after destination acceptance and leave the old home as a redirect, never two active truths. Dependencies and contributions are separate links, never extra parents. Containment and dependency cycles are refused. A finishing container cannot parent standing work; an extracted playbook attaches to a standing ancestor or the project root, with a spawn link to its source campaign.
- **Placement is distinct from ancestry.** The registry locates projects, and catalogs locate campaign/playbook folders; folder nesting never invents a parent. A task needs no folder. Container bodies use the forms in `estate-structure.md`; a project home is the project itself.
- **Records and invariants stay outside the tree.** People, facts, assessments, and rules are records or conventions that work references, never copies. A rule that never completes is not a recurring task.
- **Capture stays light.** Id, kind, home, and title suffice at intake; preserve the user's wording with detail separate. Classify before execution. Uncertain classification is `unclassified`, visible for reconciliation. Residual counts feed the vocabulary's revision signal, with a ceiling in the engine's config (`engineering-standards.md`).

## Lists and ranking

- One `TODO.md` per workspace, at the root, headed `# TODO (ordered)`. The hub's list is the estate head; project lists are tails. A head entry referring to a tail is a projection or pointer to the same node, never a second task.
- **Position = priority.** Active-list order is the user's ranking, with no competing priority-label system. Machine assessments remain separate. Pins record the user's explicit ordering instructions.
- **Adding never reorders.** Append to the tail or a capture inbox. Ranking happens deliberately in batch passes; an explicit instruction to place or pin an item first is honored.
- **Grasp the big, release the small.** Selection drops or shrinks minor work; sequence keeps major work from waiting behind it.
- Task lists are working state. Keep them out of shared version control unless the team explicitly runs a shared list. Every session records completions and material advances through its list's current write surface.
- Task files and records use plain English, translating at intake without glosses; human names may keep their native script.
- **Cite items to the user by position, never by id:** "item 2" plus a few words of its text. Stable ids are tooling addresses only.

## States (before scores)

Only **active** items compete for order. Other live states remain visible in their own sections:

- **dormant `[after: YYYY-MM-DD]`**: code wakes it on that date.
- **dormant `[when: <event>]`**: a session wakes it after checking evidence that the event happened.
- **`[waiting: <who/what>]`**: a typed dependency, event, or reference to the exchange on its sanctioned surface. Elapsed silence never resolves a wait; this creates no person or thread store.
- **someday**: kept without commitment.
- **review**: awaiting an assessment or decision, with the next reviewer and question explicit.

Closed nodes leave live lists and remain in history. `done` and `dropped` are terminal states; a withdrawal uses `dropped` with the distinct `withdrawn` disposition below. Unknown states fail validation and surface for reconciliation.

## Annotations (optional, coarse)

- `[due: YYYY-MM-DD hard|near-hard|soft]`: a deadline's WALL date. A bare date means hard; older hard/soft tags stay valid. Multiple or uncertain deadlines use rows, never invented dates in tags.
- `[value: A|B|C]`: coarse value tier.
- `[~30m|~1h|~2h|~days|~weeks]`: effort.
- `[brain: low|med|high]`: cognitive drain, not duration.
- `[added: YYYY-MM-DD]`: stamped on first capture.
- `[unlocks: <what>]` · `[sooner-better]` · `[idea]`: routing hints.
- `[cadence: Nd|Nw]` or `[checks: d1, d2, …]` + `[checked: YYYY-MM-DD]`: held between checks; exhausted checks need extension or closure.
- `[escalate: YYYY-MM-DD]`: forces top urgency if unresolved on that date.
- `[parent: <node reference>]`: optional containment annotation, including the home project when needed for uniqueness.

Urgency and action dates are computed at read time, never stored as task fields.

## Deadlines and the wall map

**Deadlines have their own rows**, many per node, each kept once and deduplicated by stable row id. Fields: node reference · date (time and timezone when relevant) · strength `hard / near-hard / soft` · origin `stated / derived` · knowledge `dated / unknown` · source citation · checked-on stamp · applicability condition · revision. Near-hard means movable only at the other party's discretion, with real options lost if missed. A derived row needs its assumption; an unknown date needs a resolver, either a task that can establish it or an evidenced event condition. Soft targets create no deadline pressure. Revisions append history with supersession links, never erase an earlier wall.

**Wall map first.** Before planning a matter with deadlines, assemble and check its rows, its children's rows, and directly relevant dependency rows. Map state is `unassessed`, `assessed-with-rows`, or `assessed-none`; a missing date tag never proves there are no walls. Unrelated pursuits enter only on the user's word or through a direct dependency. Store the map revision used by the plan. A new, revised, or removed applicable wall invalidates that plan revision before the next move executes. An unassessed campaign remains visible with a warning, but its executable moves are withheld; other work still renders.

**The action date is derived.** For an action against an external wall, use the wall minus the larger of **two days** and the evidenced lead time for preparation or external latency, working backward through dependencies. A lead time that cannot fit raises a conflict. The `[due:]` tag holds the wall; prose plans and action views show the derived action date, never a second hand-written task date. This applies to submissions, filings, registrations, renewals, and payments. A window whose start the user controls stays an anchor-plus-offset row until planning fixes the anchor; it creates no premature wall.

In markdown, keep structured deadline rows beside the list or in a container's declared block, with one authoritative row per id. An existing `[due:]` tag is a compatibility input: at the next wall-map pass, assemble its row, verify source and strength, then keep the tag consistent with the row. Existing list text needs no mass rewrite.

## Transitions and dispositions

Check for an existing node before founding another. One independently executable action is a task; several moves needing continuing coordination or a strategy choice that closes options earn a campaign with a named end. Promotion from task to campaign preserves the id and makes the original action its first move. A campaign growing into a project records that transfer and its residue. An empty child list or a clean worker exit is never completion evidence.

**Close records data, not just an archive sentence.** Every close writes a disposition: `done / dropped / withdrawn`, evidence against the named end or retirement criteria (labeled verified or judged), and typed residue. Residue is explicitly `none`, or a list of remaining obligations with each destination's node kind, stable reference, and home. A campaign's close records the user's extend, resize, or close decision. Files stay marked closed. Append one line to the workspace's `archive.md` (a generated archive in the store-backed form): `<close-date> · [done|dropped|withdrawn] · task text · [added: YYYY-MM-DD] · disposition reference`; a missing added date stays `[added: ?]`. These close outcomes are distinct from the execution result classes in `human-agent-collaboration.md`.

**The engine refuses these transitions.** In degraded markdown, the agent or person runs this same list as a pre-write checklist:

1. Projecting executable campaign moves with an unassessed wall map, or acting under a stale plan revision.
2. Closing a container with open children, no completion evidence, or no disposition accounting for all residue.
3. Founding a campaign without a named end.
4. Adding a second home or parent, a cycle, or standing work under a finishing parent.
5. Accepting a derived deadline without an assumption or an unknown date without a resolver.
6. Writing directly to a generated view, or mutating over an un-ingested edit to one. The user's edits use the controlled intake below.
7. Mutating against a stale node revision or execution-claim generation.

Kind, rank, pin, eligibility, a claim, and a successful run grant no permission. Per-action authority stays at the executor (`engineering-standards.md`); result handling follows `human-agent-collaboration.md`.

## The store-backed form (the standard form where a store engine exists)

Once A7 provides an engine (`store.md`), the sanctioned agent builds this contract against it. The store provides persistence, transactions, and backups; the task tool validates the model, computes dates, and renders views. Domains keep meaning and success criteria. Data follows the store's data-home layout; code, prose, and rendered views stay in project homes.

- **Task row:** stable integer id assigned once and never reused · kind · one nullable parent · home project and path · title and body reference · named end for ending containers, target and scope for standing ones · state · typed annotations · execution result class · added/closed stamps · node revision · wall-map state/revision · plan revision · claim generation. Rank and pin are the user's judgment fields; estimates remain dated assessments. Project plus id identifies a node across stores. Dependencies, contributions, and spawn links are separate typed references. Strategy and narrative logs remain authored prose, not database fields.
- **Related tables:** `deadlines` holds the rows above and their revision history; `dispositions` holds outcomes, evidence, and typed residue; `claims` holds node reference, executing agent/session, generation, acquisition and release stamps. They join `tasks` by node reference; declarations ship in `skeleton/store/schemas/schemas.yaml`.
- **Atomic claims:** `claim` grants one executor at a time, in a transaction. Every executor write checks node revision and claim generation. Release ends the claim; a deliberate takeover increments the generation so a stale worker cannot write or release its successor's claim. Timeout or silence confers no authority.
- **Append-only ledger:** every state change, note, deadline revision, claim event, and close appends a dated row with provenance. Reconciliation never erases history; close emits the disposition and archive entry in the same transaction.
- **One verb write surface:** `add · close · note · edit · state · rank · pin · wake · claim · release · show · list · regen · ingest · verify`. Stamps are automatic. `edit` addresses node and deadline fields with revision checks; `close` accepts outcome and residue; `rank` performs batch reordering. Reads never adopt or migrate a list.
- **The store is truth; all views are generated.** Render the head, per-project tails, live-matters register (all open nodes, including dormant, waiting, and review), estate timeline (including unknown and conditional rows), and campaign/playbook catalogs. Regenerate affected views after every write. Each carries a generated banner naming its source and write path, stable ids, and a source revision. TODO views retain the ordered active section followed by other live-state sections; task lines end `[id: tN]`. One node may appear in several views without another home. Missing sources produce a visible error, never "nothing due".
- **Authored extensions survive.** Free-write tail sections remain behind declared markers. Container files separate generated fields and move lists from authored strategy, standing rules, narrative logs, and conclusions. Regeneration replaces only generated blocks.
- **Hand edits are input, never a second truth.** A hash detects changes; mutating verbs refuse until `ingest` reconciles them against the recorded source revision with provenance. Reordered active lines supply user ranking, edited lines propose field changes, id-less lines create nodes, and deleted lines are reported for confirmation, never silently closed. Validate the transition refusals, then regenerate; never reconstruct the database from a rendered file during normal reads.
- **Wake is a standing job.** Dated dormancy wakes through the ledger automatically, in the engine cycle or session-opening sweep. Event dormancy still requires evidence and judgment.
- **Cut over once, keep the backup.** Parse and load existing markdown without changing its text; preserve existing ids, order, pins, dates, history, and generations. Retain the pre-flip file as a read-only backup. Assemble existing dated items' deadline rows at the next wall-map pass; missing tags import as unassessed. Rebuild an existing task tool against the new schemas at its next natural touch, preserving one writer and its compatibility entry point. Cut over only after deadline reconciliation, compatibility, claim-race, stale-writer, and recovery checks pass; older write/sync paths then refuse.
- **Verify is cheap and standing.** `verify` checks row shape, tree/link integrity, deadline/disposition completeness, claims, and view agreement with the store. The estate self-audit reads it.

Without an engine, each list has ONE hand-maintained surface. Registers, timelines, and catalogs are reads or pointers over those lists and declared row blocks, never additional editable task copies. Keep the shapes and refusal checklist so a later cutover preserves meaning.

## Cold-resume briefings

A parked task carries its resume package on its task line: what is done, exact next command ready to run, how to verify, and a checked-on stamp naming the source. A session awaiting the user's word or hands files that package before it ends (`session-discipline.md`); a board pointer alone is insufficient. A future session can resume without reconstructing the conversation.
