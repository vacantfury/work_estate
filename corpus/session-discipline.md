# Session discipline (portable)

How a working session — an AI agent session, or a person following the same discipline — stays reliable and cumulative. Tooling-agnostic.

## Type every request by its deliverable

- **Discuss** = the deliverable is words (assessment, recommendation). **Act** = the deliverable is a state change.
- **Ambiguity fails toward discuss:** assess and recommend; don't mutate state until asked.
- A discussion reply carries **one clear recommendation** with brief reasoning — a neutral option survey hands the deliberation cost back to the asker. If options genuinely tie after real weighing, say so explicitly and name the tiebreaker.
- **Multi-point deliberations go one point per round:** settle one, then move to the next — never a multi-question ballot.
- **Conclusion first, plain terms:** lead with the one-sentence bottom line; detail after. Use standard terminology, never invented paraphrases.
- **Naming rule:** a name is either SHORT (rough-but-short is fine) or long only because accuracy genuinely needs every word — medium-long and still imprecise is the forbidden zone. Things handled daily (projects, skills, commands, state files) default short; length is spent only on one-off documents where precision earns it.
- **Plans are ordered steps; only deadlines carry dates:** a forward-looking plan presented to the user lists steps in execution order with no per-step time points; a date appears only on a real deadline — an external wall, or the buffered date of the action against it (`task-convention.md`). Records and history keep their dates.
- An action mentioned in passing that would outgrow the current sitting is proposed as a filed task — never silently started as a multi-session workstream.
- **No self-initiated postponement:** the session never defers or freezes work for time reasons on its own initiative — a timing risk is named once, neutrally, while proceeding; time-based sequencing of work is the user's call alone. Build-order dependencies (a step genuinely needing another step's output) are sequencing, not postponement, and remain engineering judgment.

## Reply format

The per-reply scannable close: the user reads the state of the work off the reply's last lines, never reconstructs it from prose.

- **Status footer:** every reply ends with ONE status line, exactly one of four signs: `✅ **complete — nothing new deferred**` · `🔔 **complete — deferred: <named items>**` (every item filed during this arc named; awareness-only notes flagged as such) · `🔄 **continuing** — <what's in flight>` · `⏸ **waiting on you** — <the one thing needed>`. Binding rules: the complete bar is HIGH — ✅/🔔 require zero actionable residue (everything done, filed as a task, or asked); a dangling "want me to X?" means the reply is really ⏸, or the work should have been done or filed. Deferrals stamp ONCE, in the arc that files them — already-filed items never re-carry. The sign follows residue: none → ✅; any → 🔔 with the text immediately naming it. ⏸ outranks ✅/🔔 whenever an open ask, decision, or hands-step remains with the user. A live discussion stamps 🔄 naming it until the user's explicit completion word or a clean pivot — an interim "this is good" is never closure. A handoff to another party stamps 🔔 naming the target and expected result, with the wait recorded on the task line (`task-convention.md`), never held as conversation state; a step awaiting the user's own in-conversation action is ⏸ naming it.
- **Item manifest:** when two or more items are carried in the closing block, render ONE evolving table directly above the footer, with columns `# · Item · Type · Status`. Type is SECOND PERSON: 📖 FYI · 💬 your word · 🖐 your hands. Status: 🆕 new · 🔄 ongoing (actively advanced here) · ⏳ yours · ✅ done · 📮 filed · 🗑 dropped. Each label pairs its emoji with a word. Item numbers stay stable; open items persist and terminal items show their end state once. Below the threshold, render only the footer. Board deliveries remain exempt: their ACTION numbering is the manifest (`human-agent-collaboration.md` §The board delivery form). The record renderer below owns this block.
- **Anchor line:** a LONG reply (multi-section, or arriving after a heavy tool-work stretch) OPENS with one blockquote line restating the ask — `> **Your ask:** …` (verbatim when the ask was short; enumerated when there were several). Short direct answers skip it.

## The session record

Each session keeps ONE structured record. The agent judges what the work means; code maintains its state and renders the close. A transcript supplies evidence, not a second task list. The record links to durable tasks when work outgrows the sitting.

- **Intake:** one item per ask in the user's words, with its request type. Keep stable item numbers and the order of business. Use `start` to put an item in flight and `note` for a material advance.
- **Disposition:** `done` requires evidence labeled **verified** (execution, checker, or authoritative readback) or **judged** (a reasoned assessment). `ask` marks a need for the user's word or hands. `file` records the destination task when work outgrows the sitting; `drop` records deliberate abandonment and its reason. No successful worker exit substitutes for evidence.
- **Lane:** `interject` adds a question without changing the active lane; answer it and return to the interrupted work. `pivot` records an explicit change of lane. Corrections, facts, preferences, and decisions are observations routed to their durable homes.
- **Standing orders:** record them verbatim at receipt, restate them in the acknowledgment, and keep them binding for the whole session. After context compaction, inject them again and re-list them in the first reply. If a rule may have been lost, re-read the record rather than guess.
- **Render last:** after all record writes for the reply, `render` produces the closing block specified in §Reply format. Paste it verbatim. The stop hook checks the reply against the record, including a missing or wrong completion sign and unparked work at wrap. The agent repairs the underlying record or work, never invents a contradictory footer.

The sanctioned tooling's native hooks provide intake, stop checks, context restoration, and session-end archiving where available. With no such hooks, keep the same record and run the checks by hand; do not claim enforcement that the host cannot provide. Parking follows §Wrap protocol, including items waiting on the user before the session ends.

## Session notifier

A platform-local notifier calls attention to a completed round or a dialog that blocks progress. Adapt its command at unfold A1; the policy uses the harness's **Stop + Notification** hook pair and the latest prompt's recorded start/completion state. Timing values live in the installed config: completion minimum **120 seconds**, dialog-idle event **60 seconds**. These are notification thresholds, never work deadlines or authority timeouts.

| Event | Notification policy |
|---|---|
| Stop for the latest prompt | Record completion even for a short turn; send one "job done" ping only if that turn lasted at least 120 seconds. |
| Notification after 60 seconds idle on a question or plan-approval dialog | Ping only when no Stop has been recorded for the latest prompt, so the dialog is blocking mid-turn. |
| Permission-prompt Notification | Ping immediately; these prompts emit no later idle event. |
| Plain idle after Stop, a short completed turn, or general awareness traffic | Stay silent. |

Track prompt identity so an old Stop cannot suppress a new blocked turn or announce an unfinished one. A ping identifies the project and reason, and confers no approval. If the host lacks the required events, record the limitation at unfold; never substitute repeated idle pings.

## Verification discipline

- Claims of "done / installed / blocked" show **evidence** — actual output or state, never bare assertion.
- A checkable fact is verified against its primary source before being asserted whenever something rides on it (an action, a recommendation, a report upward) or it contradicts what someone reported. Facts recalled from memory are labeled as such ("unverified", "as I recall") — never dressed as checked.
- Never escalate a diagnosed blocker to someone else's hands without first testing the cheap path yourself; escalate only on verified failure.
- **Tool-path order:** a surface with a programmatic seam — an API, CLI, or tool integration — is read and acted on through that seam; UI/browser automation is the fallback for surfaces with no seam or whose auth exists only in the logged-in UI; a person's hands are the last resort, reserved for what only they can do. A one-time tool failure is self-repaired (relaunch, reconnect, retry) before the step converts into a human ask.
- When handing a person a manual step, deliver it execute-ready: exact command or click-path, the target end state, any text prepared ready to paste, and what to confirm afterwards. At every UI choice point, name the exact option — never leave a branch to guesswork. After they report doing it, verify the result where a tool can. Anything the person is pointed to — a page, a portal, a document, a file — comes with its direct address: the exact URL or file path, openable as given, on its own line; a described location the person must find by hand is a defect.
- **Instruction completeness for human-executed steps is the session's duty, on par with the execution itself:** a person's error under absent, incorrect, or incomplete instruction is the system's failure, never theirs — attribute and fix it system-side.
- **Strong dissatisfaction is a defect report, not a mood:** the next reply is diagnosis and fix — re-read what was actually asked, check the primary sources, locate where the work or understanding is factually wrong, deliver the corrected work in that same reply. If verification shows the work was right, stand ground plainly with the evidence. No apology paragraphs.
- Every execution arc closes with **verify · record · report faithfully**: failed tests reported as failures with output, skipped steps named as skipped, done stated plainly when verified.

## Capture at settle

- When a judgment stabilizes or a practice recurs, write it into its durable home **in the same session it settles** — conventions file, design doc, config, TODO. Sessions are stateless; an unwritten conclusion is re-derived at full cost.
- A correction received — doubly one that had to be repeated — is formalization debt: encode it durably the same session, so the next session inherits it instead of re-earning it. On any correction, the next reply leads by restating what was actually meant; the same misunderstanding corrected a SECOND time in one session → stop, no third guess: restate the actual ask in one plain sentence and get it confirmed.
- Guards against rule bloat: formalize at the second occurrence (rule of two), not the first; every rule names its consumer; a stale rule is drift — fix or delete on sight.
- When a standard, tool, or name is renamed, retired, or superseded: sweep the instruction surfaces for the old world in the same session and fix stale references.

## Form selection — match the form to who executes it

Every piece of a workflow is one of four forms:

- **code** — deterministic procedure for a machine: script; event-trigger → hook; time-trigger → scheduled job.
- **skill / instructions** — procedure for a mind: recurring, multi-step, with judgment or decision points. A "skill" with no decision points is a script in a skill costume — demote it.
- **files** — memory, never procedure: *law* (invariants; always-loaded only if they must constrain every turn, else pointed to) vs *state* (changing facts: TODO, results, logs). Changing facts never live in always-loaded instructions.
- **human gate** — steps reserved for a person: approvals, credentials, taste, physical actions. Rendered as a pause plus an execute-ready package — never automated away, never left vague.

Decision test, in order: needs judgment? no → code. Procedure or knowledge? procedure → skill; invariant → law; changing fact → state file. Only-a-human? → gate.

**Form-stamp on proposals:** a proposal to create or change any estate artifact names, in the proposing reply, its FORM (one of the four), its HOME (file/project), and the founding procedure — one stamp line. Container words ("a system", "a package", "a watch") never stand alone as the answer to what a thing is. Founding anything new is three lookups, never a bespoke process: this decision test names the form → the placement map (`estate-structure.md`) names the home → that form's founding procedure writes it (projects: `portable-skills.md` project-founding · tasks: `task-convention.md` · rules: capture-at-settle above).

## Three-tier attention — what a session is guaranteed to know

Place content by the read guarantee it needs:

- **Tier 1 — every turn:** the always-loaded instructions file (the workspace's standing conventions). Law only.
- **Tier 2 — session start:** a session board (`NOW.md`-style) of dated pointer lines a cold session must not miss. Pointers, never content; hard cap ~10 lines; **the session that resolves a pointed-at thing deletes its line the same session** — a stale board is drift.
- **Tier 3 — on demand:** TODO, design docs, state files, logs — reached via board pointers.

## Wrap protocol

On any imminent-stop signal, park every open arc at once. Each lands on its task-list line with a cold-resume briefing per `task-convention.md`: what is done, the exact next step ready to run, how to verify, and the checked-on source. Place resumptions at the top of the head through the task verbs (hand placement only for a markdown list), then add one board pointer per resumption. Existing tasks get their briefing updated, never a duplicate.

An item left waiting on the user's word or hands must land on that task-list line **before the session ends**, even without an explicit wrap signal. Record its task reference with `file`; a board or session-record row alone does not satisfy parking. Self-running work is reported as such, never turned into a needless resumption. A wrap never marks unverified work done, and the closing block still comes from `render` after the final record write.
