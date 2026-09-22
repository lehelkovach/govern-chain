# AGENTS.md (govern-chain)

Read [`docs/DEV-LADDER.md`](docs/DEV-LADDER.md) first. It is the board.

## Branches

Same model as the sibling repos (`knowshowgo`, `knowshowgo-client`):

| Branch | Role |
| --- | --- |
| **`dev`** | Integration. Everything lands here first |
| **`main`** | Production. Promoted from `dev` once tested |

- Branch from **`dev`**; PRs base **`dev`**.
- Never PR a rung into `main`. `main` moves by promotion from `dev`.

## Rules

- **Do not answer §3 of the ladder on the author's behalf.** P1–P7 are political
  commitments, not research questions with a best answer. A PR that silently
  picks one is wrong even if the code is good.
- **Do not build R3 or above** until the question blocking it is answered. Each
  blocked rung names its dependency.
- **Compose, do not fork.** Identity is HumanKey's, adjudication is TruthApp's,
  the record is KnowShowGo's. A second claim store or a parallel identity model
  is out of scope.
- Design docs only for now. When code arrives, state its language and test
  command here before writing it.

## Status vocabulary

Matches `knowshowgo/docs/DEVELOPMENT-PLAN.md`: ✅ closed on merged `dev` ·
🔄 open, work exists · ⬜ not started · 🅿️ implemented but parked ·
🚫 gated · ? claimed but not re-measured.
