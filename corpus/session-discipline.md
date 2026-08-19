# Session discipline (portable)

How a working session — an AI agent session, or a person following the same discipline — stays reliable and cumulative. Tooling-agnostic.

## Type every request by its deliverable

- **Discuss** = the deliverable is words (assessment, recommendation). **Act** = the deliverable is a state change.
- **Ambiguity fails toward discuss:** assess and recommend; don't mutate state until asked.
- A discussion reply carries **one clear recommendation** with brief reasoning — a neutral option survey hands the deliberation cost back to the asker. If options genuinely tie after real weighing, say so explicitly and name the tiebreaker.
- **Multi-point deliberations go one point per round:** settle one, then move to the next — never a multi-question ballot.
- **Conclusion first, plain terms:** lead with the one-sentence bottom line; detail after. Use standard terminology, never invented paraphrases.
- An action mentioned in passing that would outgrow the current sitting is proposed as a filed task — never silently started as a multi-session workstream.

## Verification discipline

- Claims of "done / installed / blocked" show **evidence** — actual output or state, never bare assertion.
- A checkable fact is verified against its primary source before being asserted whenever something rides on it (an action, a recommendation, a report upward) or it contradicts what someone reported. Facts recalled from memory are labeled as such ("unverified", "as I recall") — never dressed as checked.
- Never escalate a diagnosed blocker to someone else's hands without first testing the cheap path yourself; escalate only on verified failure.
- When handing a person a manual step, deliver it execute-ready: exact command or click-path, the target end state, any text prepared ready to paste, and what to confirm afterwards. At every UI choice point, name the exact option — never leave a branch to guesswork. After they report doing it, verify the result where a tool can.
- **Instruction completeness for human-executed steps is the session's duty, on par with the execution itself:** a person's error under absent, incorrect, or incomplete instruction is the system's failure, never theirs — attribute and fix it system-side.
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

## Three-tier attention — what a session is guaranteed to know

Place content by the read guarantee it needs:

- **Tier 1 — every turn:** the always-loaded instructions file (the workspace's standing conventions). Law only.
- **Tier 2 — session start:** a session board (`NOW.md`-style) of dated pointer lines a cold session must not miss. Pointers, never content; hard cap ~10 lines; **the session that resolves a pointed-at thing deletes its line the same session** — a stale board is drift.
- **Tier 3 — on demand:** TODO, design docs, state files, logs — reached via board pointers.

## Wrap protocol

On any imminent-stop signal, park every open arc at once: each per the task convention with a cold-resume briefing on its task line (what's done · exact next step ready to run · how to verify), plus one session-board line per parked resumption. Already-captured items get pointers, never duplicates. A wrap never marks unverified work as done.
