# govern-chain

**GovernChain** is a design for decentralized governance: turning an evaluated
argument graph plus a set of verified humans into a binding decision that
carries its reason.

This repository holds the design record. **Nothing is implemented yet.**

## Documents

| Document | What it covers |
| --- | --- |
| [`docs/DEV-LADDER.md`](docs/DEV-LADDER.md) | The ladder. R0–R2 are specifiable now; R3–R7 are blocked on the seven questions in §3 |
| [`AGENTS.md`](AGENTS.md) | Branch model and rules for anyone — human or agent — working here |

## Why this is not a blank page

Three substrates governance needs already exist, in repositories that ship:

| Need | Substrate | State |
| --- | --- | --- |
| Who may participate, provably once | [`human-key-core`](https://github.com/lehelkovach/human-key-core) — soulbound identity, proof-of-personhood, consent-gated use, revocable | design only |
| How disagreement is adjudicated without an authority | [`truth-app`](https://github.com/lehelkovach/truth-app) — grounded argumentation over SUPPORTS / REBUTS / UNDERCUTS, premise support, deterministic evaluators | working |
| The durable, provenance-bearing record | [`knowshowgo`](https://github.com/lehelkovach/knowshowgo) — immutable assertions, revisions, Logic IR with canonical hashing | working |

GovernChain composes them. It is not a fourth stack.

## What only the political philosophy settles

The ladder's §3 lists seven questions — standing, whether reputation may weight
a vote, what a constitutional overlay constrains, what legitimacy means, whether
a polity may be forked, what is non-delegable to an AI, and what a defeated
minority position is owed. Each is a fork where the engineering follows the
politics. They are left open rather than guessed.

## Status

Design only. No code, no dependencies, no build.
