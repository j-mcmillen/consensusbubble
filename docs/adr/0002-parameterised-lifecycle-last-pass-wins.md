# One proposal lifecycle, parameterised by policy, with last-pass-wins concurrency

Every Proposal kind — setting change, detail change, content post, membership change, moderation action — moves through the same state machine (Open → Passed / Failed / Withdrawn) under the same rules from ADR-0001. What varies is parameters, not mechanics: a **Proposal Policy** (today just Voting Window length) is resolved most-specific-first — per-subject → per-kind → Bubble default — and policies are themselves settings changed by consensus. Concurrent Proposals against the same subject are allowed with **last-pass-wins**: each applies at its expiry, so the latest expiry ends up in force.

## Considered Options

- **Per-kind state machine variants** — rejected: the lifecycle stops being one concept and every downstream mechanic (propagation, deadlock, moderation) must handle each variant.
- **One live proposal per subject (locking)** — rejected: adds gatekeeping machinery and queueing; the veto system is the filter.
- **Stale-fails optimistic concurrency** — rejected: a hidden failure mode members would have to learn.

## Consequences

- Members may be judging a proposal while the underlying state changes beneath it; the veto comment is the place to say "this no longer makes sense".
- Any member can propose anything from the moment they join — no tenure or sponsorship gates; flooding defences belong to moderation (issue #12).
- There is no draft state: submission opens the window immediately, and a proposer who wants a hold Self-Vetoes.
- Which policy knobs are consensus-changeable vs invariant is decided by meta-governance (issue #6).
