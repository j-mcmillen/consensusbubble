# Veto-only consensus with silence as consent

Consensus inside a Bubble needed a decision rule; the alternatives were affirmative unanimity, consent-with-quorum, and supermajority. We chose pure veto-only voting: there are no yes votes and no abstentions — a Proposal passes when its fixed Voting Window (per-Bubble setting, default 48h) expires with zero standing Vetoes. Silence is unconditionally consent, with no quorum or seen-requirement; the window length is the Bubble's only safeguard.

## Considered Options

- **Affirmative unanimity** — rejected: every inactive member becomes an accidental veto, freezing the Bubble and every level above it.
- **Consent with a seen/quorum threshold** — rejected for simplicity: a dormant Bubble rubber-stamping content is accepted as a known risk.
- **Supermajority** — rejected: tolerating dissent breaks the premise that the community reaches consensus before any change; dissenters split instead.

## Consequences

- Dissent must be expressed, with a reason: every Veto carries a mandatory comment.
- Vetoes are durable within a Proposal: they survive Adjustments (which restart the full window) and clear only by the vetoer's Retraction — so passing an adjusted Proposal means convincing each vetoer, and an intransigent vetoer can block indefinitely (handled by the deadlock rules, issue #9).
- A failed Proposal is retried by Resubmission, which carries nothing over.
- Discussion never decides: every Proposal has a Discussion Thread, but only Vetoes affect the outcome.
