# GovernChain — dev ladder v0.0.1 (draft)

**Status:** scaffold. R0–R2 are specifiable; R3–R7 are blocked on §3.
**Written:** 2026-09-21.

## What this was built from, and what it is missing

This ladder was assembled from everything about governance available in the
session: the `GovernChain_Whitepaper.md` stub in the AI Whitepaper Bundle
(twelve lines), the HumanKey v0.9 technical design, and the argumentation
machinery that already works in TruthApp.

**It does not contain your cyber sovereignty liberalism material.** No
political-philosophy writing reached this session — the three shared chats
covered the HumanKey TDD, a graph-ORM question, and the prototype-matching /
Logic IR handoff. So nothing here is "merged from your better ideas"; every
philosophical commitment below is either (a) already implemented in TruthApp
and merely *named* here, or (b) marked `NEEDS-PHILOSOPHY` and left open.

Read §3 first. Those are the questions your political philosophy answers, and
until it does, the rungs above R2 cannot be specified — only guessed.

---

## 1. GovernChain is not a blank page

The whitepaper stub names four concepts — reputation-aware governance,
constitutional overlays, governance DAGs, adaptive voting — with no mechanism
under them. But three substrates that governance needs are already built and
tested, in repositories that exist:

| Need | Substrate | State |
|---|---|---|
| Who is entitled to participate, provably once | **HumanKey** — soulbound identity, proof-of-personhood, Sybil resistance, consent-gated use via the Guardian Agent, revocable and rebindable | design only (`human-key-core`, v0.9 TDD) |
| How disagreement is adjudicated without an authority | **TruthApp** — grounded argumentation over SUPPORTS / REBUTS / UNDERCUTS, premise support, structural findings, deterministic replaceable evaluators | **working, 75 tests** (`truth-app`) |
| What the durable, provenance-bearing record is | **KnowShowGo** — immutable assertions, revisions, provenance overlays, Logic IR with canonical hashing | **working** (`knowshowgo`, `knowshowgo-client` v0.2.20) |

GovernChain is the composition layer over these, not a fourth stack. Its job
is to turn *an evaluated argument graph* plus *a set of verified humans* into
*a binding decision with a reason attached*.

## 2. Commitments already implemented that are quietly political

TruthApp's architecture decisions are not neutral engineering choices. Four of
them are substantive positions on how a polity should reason, already enforced
in code. They are the strongest candidates to carry upward into GovernChain,
because they are the ones that have survived contact with an implementation.

| Decision | As implemented | Read politically |
|---|---|---|
| **D5** No universal truth score | Labels are accepted / rejected / undecided per argument, established / defeated / open per claim. Never a scalar. | The system refuses to rank speakers or issue a single verdict. There is no seat for a sovereign arbiter to sit in, because the schema has no field for one. |
| **D10** Permissive ingestion, strict evaluation | A claim may exist with `basis: assumption` and no sources; the evaluator reports that, never silently drops it. | Wide latitude to speak; narrow latitude to *bind*. Expression is unpoliced; consequence is earned. |
| **D17** Equivocation is a grounding fact, not a rhetorical accusation | `W001` fires only when one symbol is bound to two concept ids inside one argument. | Converts "you are arguing in bad faith" into "this term is bound twice." Depersonalises the most common deliberation failure. The strongest idea in the stack for governance. |
| **D16** Grounding is exact label/alias only; ambiguity stops | `resolveTerm` returns candidates and leaves the term ambiguous. No embedding similarity, no LLM pick. | No machine silently decides what a contested word means. Semantic commitment is an explicit, attributable act. |

Also load-bearing: **semantic commits, branches and diffs** already exist
(D19). A constitutional amendment is structurally a branch off `main@n` with a
semantic diff and an evaluation diff — that machinery is built and tested, not
hypothetical.

## 3. What only your political philosophy can settle — `NEEDS-PHILOSOPHY`

These are not research questions with a best answer. Each is a fork where the
engineering follows the politics, and picking one silently would be me writing
your philosophy for you.

| # | Question | Why it forks the build |
|---|---|---|
| P1 | **What confers standing?** One verified human, one voice? Stake? Demonstrated competence in the domain? Being an affected party? | Decides whether HumanKey's proof-of-personhood is *sufficient* for enfranchisement or merely *necessary*. Changes the identity integration entirely. |
| P2 | **May reputation weight a vote?** The whitepaper says "reputation-aware governance"; equal suffrage says no. | This is the sharpest liberal tension in the stub. If yes, reputation needs a provenance-bearing definition and an appeal path. If no, reputation may only *route attention*, never *count*. |
| P3 | **What does a constitutional overlay constrain, and who amends it?** | Determines whether the constitution is data inside the graph (amendable by the same process it governs) or a separate artifact with a higher bar. Branch semantics differ completely. |
| P4 | **What is legitimacy?** Procedural (the process was followed), consent-based (the bound parties agreed), or outcome-based? | Decides what a `Decision` object must carry to be valid, and what makes one void. |
| P5 | **Is there a right of exit — can a polity be forked?** | "Cyber sovereignty" implies yes. If so, forking is *secession*, and the branch/merge machinery inherits a political meaning it does not currently have. Also decides what a fork owes its parent. |
| P6 | **What is non-delegable to an AI?** | TruthApp's D7 already says AI output is proposed, never silently accepted. Governance needs the stronger version: which acts require a present, consenting human, verified by HumanKey. |
| P7 | **What happens to a defeated minority position?** Preserved with standing, archived, or discarded? | TruthApp keeps `defeated` arguments in the graph rather than deleting them. Whether that is a *right* or an implementation detail is a political call. |

## 4. The ladder

Rungs R0–R2 are specifiable now, because they depend only on substrates that
exist and on commitments already implemented. Everything from R3 is blocked on
§3 and is sketched only to show where the answers land.

| Rung | Deliverable | Depends on | State |
|---|---|---|---|
| **R0** | **Vocabulary.** A `Decision`, `Motion`, `Deliberation`, `Polity`, `Franchise` object set, defined as KSG prototypes the way Logic IR primitives are seeded — matched, never hard-typed. | KSG prototype matching (shipped) | specifiable |
| **R1** | **Deliberation → decision.** Take a TruthApp snapshot at a commit, read its grounded labels, and emit a `Decision` that pins the commit hash, the evaluator id + version, and the argument that carried. No voting yet. | TruthApp evaluator (shipped), KSG (shipped) | specifiable |
| **R2** | **Provenance of a decision.** `explain(decision)` walks back to the claims, the attacks that failed, and the grounding choices — reusing TruthApp's existing explain/diff path. A decision nobody can explain is not a decision. | R1 | specifiable |
| **R3** | **Franchise.** Bind participants to HumanKey identities; a ballot is a consent-gated, Guardian-signed act. | **P1, P2, P6**, HumanKey implementation | blocked |
| **R4** | **Voting.** Whatever P2 decides. If equal suffrage: one verified human, one voice, Sybil-resistant by construction. If weighted: reputation needs a definition, a lineage and an appeal. | **P1, P2**, R3 | blocked |
| **R5** | **Constitutional overlay.** Constraints that a `Decision` is checked against before it binds — as a branch, or as a separate higher-bar artifact. | **P3, P4**, R1 | blocked |
| **R6** | **Amendment.** Semantic commit + diff against the constitution, with whatever threshold P3 sets. Machinery exists (D19); the threshold is political. | **P3**, R5 | blocked |
| **R7** | **Exit / fork.** Secession semantics: what a forked polity carries, what it owes, whether the parent's decisions still bind. | **P5**, R6 | blocked |

## 5. What is deliberately not here

- **A consensus protocol.** The stub says "governance DAGs" and HumanKey's TDD
  has a DAG/L2 auth chain. Whether GovernChain needs a chain *at all*, or is a
  protocol over KSG's existing provenance, is an open architectural question —
  and answering it before P3/P4 would be building the mechanism before the
  legitimacy it is supposed to serve.
- **Any political philosophy of mine.** §3 stays open rather than guessed.

## 6. Immediate next step

Supply the cyber sovereignty liberalism material and the cyber governance
architecture. Then §3 is answered from that writing rather than left open, §2 is
checked against your stated commitments rather than inferred from TruthApp's,
and R3–R7 become specifiable in the same style as R0–R2.

Until then the buildable work is R0–R2, which depend only on substrates that
already ship.
