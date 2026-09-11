# Agent reliability

Working conventions for building and evaluating agentic LLM features, distilled from the peer-reviewed reliability/safety literature (each point cites its sources directly; evidence tiers: A = top-venue peer-reviewed, B = strong preprint/audit, C = weaker or unreplicated). **Provisional by provenance:** written pre-start from public literature; the concrete form is resolved only after seeing the team's real docs and workflows — where the employer or team has an established standard, the team standard wins, and the unfold treats each section as adopt / adapt / fold-away like any other module.

The literature sections retain their cited provenance. The permission-policy section is an operating convention from settled practice, adapted to the sanctioned host tooling at unfold.

The one-sentence thesis the evidence supports: **every reliably-working approach puts something outside the model in the loop — a test, a compiler, a permission system, a human; everything that asks a model to police itself either fails or is unvalidated.**

## The verification ladder

- **Where a real checker exists at reasonable cost, use it — always preferred.** Unit tests, execution, proof checkers, state readback. The strong results all have this shape: test-gated code agents (SWE-bench, ICLR 2024 oral, A), proof-checked math (AlphaProof/Lean, Nature 2025, A), process supervision against checkable steps (Lightman et al., ICLR 2024, A). A claim so anchored is *verified*.
- **Where no checker exists, use the best judge that does exist — model judgment is legitimate and often the strongest available.** Don't fear heuristic review; raise its quality by form: judges from a different model family than the generator, diverse review lenses over identical skeptics, evidence-citing review over bare opinion. A claim so supported is *judged* — an honest label, not a second-class one; it tells the consumer which kind of confidence they hold.
- **Never let a model clear its own work.** Intrinsic self-correction without external feedback is a settled negative — models talk themselves out of correct answers (Huang et al., ICLR 2024, A; TACL 2024 survey). Same-family LLM judges systematically favor their own family's outputs, and the bias scales with self-recognition ability (Panickssery et al., NeurIPS 2024 oral, A).
- **A completion claim is a model assertion, not a fact.** An agent's "done, it works" gets reported upward only after a state readback — a clean exit code or a confident summary is not evidence.
- **The human enters for authority, not epistemic rescue:** approval on irreversible/consequential steps and domains where the human genuinely is the stronger judge; every escalation carries the system's recommendation, because the epistemic work belongs to the system.

## Structural vs heuristic controls

- **Know which kind every control in the system is.** Structural = cannot be prompted around: permission systems, sandboxes, capability control, a single enforcement choke point, type/proof checkers (CaMeL; OS-level isolation — IsolateGPT/SecGPT, NDSS 2025, A). Heuristic = a model or prompt convention that can drift or be evaded: prompt rules, classifier guardrails — evadable at reportedly up to 100% via encoding tricks (tier C red-team studies).
- **Anything consequential rides a structural control;** heuristic layers are for quality, never for safety-critical guarantees. Structural cost is real and worth paying knowingly (CaMeL trades 84%→77% task success at ~2.8x tokens).
- **Text-safety training does not transfer to tool-call safety** ("Mind the GAP", tier C) — distribution shift for agents lives in tool/environment space, not just input text; safety measured on chat transcripts says little about an agent with tools.

## One permission policy

The estate keeps ONE policy file, with each rule mapped to every sanctioned host's native tool controls. It declares the deny list, protected-zone patterns, the person-facing ask list, live-session guards, and host enforcement coverage. Host settings are links or renders of that policy's intent, never independent policy sources. A host capability gap is recorded explicitly; a prompt rule is not evidence of a structural control.

- **Deny destructive system operations.** System-root removal, disk formatting, privilege escalation, machine shutdown, and process-exhaustion commands never run through an agent, even on request. If such an operation is necessary, the user runs it by hand.
- **Protect user-only zones by every path.** No agent reads, lists, searches, or writes their contents through a file tool, shell, alternate path, or tool integration. The zone rule is defined in `boundary-protocol.md` §User-only zones. Audit pattern coverage without opening the zones.
- **Keep the native ask list to person-facing sends and RSVPs.** It is the final-press backstop: prepare the exact content and leave the press to the user. Other operations within the task's authorized scope run unprompted, subject to the deny list, sandbox, and existing authority gates. An allowed tool call is never new authority to publish, spend, register, or commit the user externally.
- **Guard live working sessions.** An agent never kills the user's sessions, editors, or shells holding open work, however old or idle they appear. Enforce this before process-management calls, failing closed for the protected class; never propose a kill list to free resources.
- **Never disable the sandbox or approvals to make a run work.** Resolve the host's supported policy mapping at unfold; use the allowed subset when a required control cannot be enforced. The two-agent convention in `human-agent-collaboration.md` uses the same policy.
- **Audit the mapping.** Compare actual host configs, native guards, and scoped overrides against the canonical policy. Report missing rules, unclassified entries, disabled controls, and unproven path coverage. Unknown entries fail toward attention, never broaden permission. The audit is read-only and never tests protection by accessing protected content.

## Trajectory-level failure thinking

- **Evaluate at trajectory level, not step level.** pass^k (all k trials succeed) is the reliability metric, not pass@1: a top function-calling agent above 60% pass@1 falls below 25% at pass^8 (τ-bench, ICLR 2025, A).
- **Agent failures are architectural, not noise:** they recur identically across trials rather than averaging out; agents pick similar action *types* run-to-run but vary the *ordering* — "what but not when" (Princeton agent-reliability program, tier B).
- **Capability and reliability are decoupling:** industry-wide, months of accuracy gains produced only small, uneven reliability gains; a capability benchmark score is not a reliability claim.

## Irreversibility and the rollback gap

- **There is no undo for actions that leave the system** — the rollback gap is open research (only incompatible early preprints exist); human approval before the irreversible step is the production answer.
- **Classify actions by their most irreversible observable effect** — three classes: `reversible` (undoable by the system), `recoverable` (undoable with effort — the class is only valid with recovery path and cost stated), `irreversible` (sends, spends, publications, anything another human observes). Judged in the world's frame, not the artifact's: a deleted message was still seen. Uncertain → `irreversible`, fail closed.
- **Irreversible steps get human approval; the class is named at the approval point,** so the approver knows which kind of yes they are giving.

## Eval and benchmark skepticism

- **Benchmark scores overstate reliability through at least three independent routes:** cost-blind benchmark design (Kapoor et al., TMLR 2024, A); outcome-validity flaws in 7/10 audited popular agent benchmarks (Agentic Benchmark Checklist, tier B); and vendor self-corrections of flagship benchmarks (OpenAI's SWE-bench Verified retraction — a majority of audited hard problems had flawed tests).
- **Trajectory judging is not production-grade:** on real agent traces, the best models localize the true error only ~11% of the time (TRAIL, tier B) — an LLM judge over agent logs is a triage aid, not an oracle.
- **More test-time compute buys capability, not reliability** — and longer reasoning *degrades* out-of-distribution accuracy (inverse scaling in test-time compute, TMLR 2025, A). "Think harder" is not a reliability strategy.
- **Confidence signals need external calibration:** verbalized confidence is badly calibrated and prompt-sensitive; semantic-entropy-style methods (Nature 2024, A) help on single answers but read repeated paraphrases of the same wrong answer as confident; activation probes fail to transfer cross-domain (tier A critique, 2025). Trust a confidence signal only after calibrating it against human labels on your own distribution — same discipline as any LLM judge.

## Operating defaults when compute budget is rich

The ladder above is stated as knowledge; where token/compute budget is not the binding constraint (typical inside a well-resourced employer), it becomes an operating default — verification on by default, skipped by exception, rather than added by exception:

- **Every substantive working-agent run is followed by an independent verification pass.** With cheap tokens the cost threshold for running one drops to near zero; what stays tiered is the KIND of check (real checker first; a judge only where no anchor exists), never whether one runs. Trivially mechanical steps are the exception, not consequential ones.
- **Monitor passes come from a different model family than the worker** wherever the sanctioned tooling offers more than one family — free adversarial diversity that directly counters same-family self-preference (Panickssery et al., NeurIPS 2024 oral, A).
- **Anything that ships gets an adversarial pass as a named pipeline stage** — a red-team pass prompted to refute and break, not to review politely; its findings triaged like test failures. Only worth its cost if genuinely independent of the generator (the self-clearing negative above).
- **Reliability claims quote pass^k over repeated trials, never pass@1** (τ-bench, ICLR 2025, A) — with a rich budget the k trials are affordable and the honest default.
- **Budget shifts thresholds, never kinds:** more compute buys more and cheaper verification passes and repeated trials; it does not upgrade a judged claim to verified (only an external anchor does), and "think harder" remains a capability strategy, not a reliability strategy (inverse-scaling result above).
