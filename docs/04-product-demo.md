# 04 — Product & Demo

## What's live today at qzn.app

| Game | What it is | Status |
|---|---|---|
| **snaQe** | Qubic-themed snake | Live |
| **paQman** | Qubic-themed pac-man | Live |
| **TANQ-Battle** | Tank arena | Live |

Backend tracks match results, XP, leaderboards, sessions. Three games run today without the token because the games are products first.

## Main user flow

**Try the games before evaluating the proposal.** Five-minute test:

1. Visit [qzn.app](https://qzn.app)
2. Play one round of snaQe
3. Check the leaderboard
4. That's the user experience the Constellation will settle on-chain post-launch

**Post-mainnet user flow:**

1. User visits qzn.app
2. User selects a game and starts a match
3. Match completes — server generates cryptographically-provenanced result
4. Result published to operator queue
5. Operators (Rust nodes) independently validate, sign attestation, submit to chain
6. N-of-M attestation threshold met → `QZN_GameCabinet` triggers settlement
7. `QZN_RewardRouter` distributes: 70% to winner, 20% to accumulator, 5% to burn, 5% to operators
8. Accumulator flushes at epoch boundary into dividends/operations/grants/burn/reserve streams

## MVP scope for mainnet launch

| Component | Status | Path to mainnet |
|---|---|---|
| Three live games (snaQe, paQman, TANQ-Battle) | Live at qzn.app | Polish under M3 |
| Six smart contracts deployed | Testnet 26–31 | Constellation refactor under M2; audit under M1 |
| Constellation pattern (deterministic governance) | Implemented in Token v2 | Apply to remaining 5 contracts under M2 |
| QZN utility token | Designed, tokenomics locked | Integrate across contracts under M5 |
| Builder portal | Designed | Build under M4 |
| Node network (Rust operators) | Designed | Build after contract refactor, 3–4 weeks |
| Tournament infrastructure | Designed | Operational at launch under M6 |
| QSWAP liquidity pair | Coordination with Spike | Seeded at launch under M6 |

## The Constellation, in one paragraph

Six contracts. Each has a `PULSE_INDEX` 0–5. On every epoch, one of them is "in pulse" (selected by `epoch() % 6`). During its pulse epoch, that contract's SC-share holders vote the burn rate between 20% and 40%. Off-pulse epochs use 25% baseline burn. The other routing percentages are fixed in `constexpr` and cannot be changed without a public contract migration.

**This is what we mean by deterministic governance.** No contract has continuous control. Burn is bounded. Routing is fixed. The pulse moves on every epoch.

## The six contracts

| Slot | Contract | Job |
|---|---|---|
| 0 | `QZN_Token` | Supply, vesting, fee accumulator |
| 1 | `QZN_RewardRouter` | Routes match settlements |
| 2 | `QZN_GameCabinet` | Registers matches, triggers settlement |
| 3 | `QZN_Nodes` | Operator registry, stake mechanics, work tracking, slashing |
| 4 | `QZN_TournamentEngine` | Tournament brackets, prize routing |
| 5 | `QZN_TreasuryVault` | ICO ignition, multi-sig, builder grants |

All six deployed at testnet indices 26–31. Internal audit findings being remediated pre-external (named in [10 — Risks & Security](./10-risks-security.md)).

## What we want the Board to see at the protocol level

- `QZN_Token.cpp` — the `SettleMatch` routing constants and constellation pulse logic (refactor complete, 50/50 procedure tests green)
- The full test suite (Token v2 procedure suite + pre-refactor baseline for the remaining five contracts; constellation pattern application scoped under M2)
- The deployed contracts at testnet 26–31
- The three live games at qzn.app

GitHub: [github.com/dutt9145/qzn-core-lite](https://github.com/dutt9145/qzn-core-lite). If the Board wants a screen-share walkthrough, contact me at duttenhefer25@gmail.com.

---

# Node Network Architecture

QZN nodes are infrastructure service providers that perform match validation, tournament hosting, and protocol operational work. Nodes are built in Rust and operated by independent participants who commit operational capital and perform technical labor in exchange for service compensation.

## What nodes actually do

Operators perform three categories of technical work:

- **Match validation.** Operators independently verify match outcomes reported by the QZN backend, perform deterministic re-computation of match state from signed inputs, and submit signed attestations on-chain before settlement executes through `QZN_GameCabinet` and `QZN_RewardRouter`.
- **Tournament infrastructure.** Operators run tournament bracket logic, validate tournament entries, and coordinate prize distribution through `QZN_TournamentEngine`.
- **Governance attestation.** Active operators vote on node-network operational parameters within bounded ranges defined in `QZN_Nodes` contract code.

## How operators are compensated

The 5% of standard match value routed to node operators (per the BPS table in [07 — Business Model & Pricing](./07-business-model-pricing.md)) is distributed **proportionally to validation work performed in each epoch**. Per-event compensation rates are identical across all tiers. **Operators who perform no validation work earn zero, regardless of stake size.**

This is service compensation for technical labor, not investment return on capital deployed.

> **Implementation note.** The work-based attribution model described above represents the finalized Nodes architecture and replaces the legacy stake-tier-multiplier model found in the original `QZN_Nodes` prototype. The contract refactor implementing work-tracking, proportional epoch payouts, and slashing logic is M2 scope, scheduled for completion before mundus_tj85 audit kickoff.

## Three operator tiers, distinguished by commitment

All three tiers are compensated using the same per-event mechanism. Higher tiers earn more because they perform additional work categories and receive priority access to validation assignments — not because they have a different pay rate for identical work.

| Compensation source | Genesis | Rent | Regular |
|---|---|---|---|
| Match validation | Eligible, priority assignment | Eligible | Eligible |
| Tournament infrastructure hosting | Eligible | Not eligible | Not eligible |
| Governance attestation | Eligible | Eligible | Not eligible |

| Tier | Stake (operational collateral) | Min service period | Distinguishing feature |
|---|---|---|---|
| Genesis | Higher commitment | 24 months | Founding partner status, elevated governance weight |
| Rent | Medium commitment | 12 months | Standard operator status |
| Regular | Lower commitment | 3 months | Permissionless entry above stake threshold |

At base-case operational scale, Genesis operators earn approximately 3x what Regular operators earn — this differential reflects approximately 3x the work performed across additional service categories, not a 3x pay rate for identical work. Stake amounts are finalized pre-mainnet in coordination with audit findings and operator availability.

**Stake is operational collateral, not investment.** Stake secures the operator's service commitment to the protocol. Stake is returned in full on graceful exit after the minimum service period. Early exit or proven malicious behavior triggers 20% stake forfeiture.

## Architecture: Rust nodes + Qubic infrastructure

QZN operator nodes are independent Rust services that interact with the QZN protocol through Qubic's RPC interface. Each operator runs their own infrastructure hosting the Rust node software.

**The work flow:**

1. Match completes on the QZN backend, generating cryptographically-provenanced match data
2. Operator's Rust node retrieves match data, performs deterministic validation, and produces a signed attestation
3. Rust node submits signed attestation to `QZN_Nodes` via Qubic RPC
4. Once N-of-M operator attestations are received for a match, settlement triggers through `QZN_GameCabinet` and `QZN_RewardRouter`
5. Per-operator work counts are tracked in `QZN_Nodes` state for proportional compensation at epoch close

**Relationship to Qubic infrastructure:** QZN operator nodes are independent service providers that interact with Qubic via RPC. They are **not** Qubic Computor nodes (the 676 entities running Qubic network consensus). They operate at the application layer.

## Qubic Oracle Machine integration for randomness

QZN integrates with Qubic's native Oracle Machine infrastructure for verifiable randomness rather than using a randomness smart contract (RANDOM). This decision reflects sound engineering: smart contract randomness is notoriously difficult to do correctly, and Qubic's oracle-provided randomness is validated through the same Computor consensus that secures the network itself.

Oracle-provided randomness powers:

- **Tournament bracket seeding** — fair, verifiable matchups
- **Random validator assignment** — pseudo-random selection of which operators validate which matches, defeating collusion by making it impossible to predict which subset of operators will be assigned to any given match
- **Match-result tiebreakers** — for any edge case requiring random resolution
- **Builder game randomness** — third-party published games can access oracle randomness through documented interfaces

This integration positions QZN as forward-compatible with the most recent Qubic ecosystem infrastructure rather than depending on legacy patterns.

## Collusion mitigation

Node operators are a concentrated decision-making layer. To prevent collusion:

- **Multi-operator attestation requirement.** Match settlements require N-of-M operator signatures before executing on-chain. A colluding subset must control N+ operators to manipulate.
- **Oracle-driven random assignment.** Validator-to-match assignment is pseudo-randomized per epoch via Qubic Oracle Machines. Collusion requires controlling enough operators to overcome random selection probabilistically.
- **Public attestation history.** Every operator decision is recorded on-chain. Pattern analysis exposes consistent outlier behavior over time.
- **Slashing for proven malice.** Operators demonstrated to have validated incorrect settlements lose 20% of stake.
- **Founder + multi-sig emergency override.** In catastrophic situations (security incident, demonstrated systemic collusion), founder + multi-sig can invoke emergency procedures including operator removal. Override invocation is publicly disclosed with reasoning.

## Three-tier governance

QZN operates a three-tier governance structure with bounded authority at each level:

| Tier | Authority | Scope |
|---|---|---|
| Node operators | Operational network parameters | Validation thresholds, payout split mechanics within fixed total — bounded by smart contract code |
| SC-share holders | Burn rate per epoch | 20–40% during Constellation pulse |
| Founder + multi-sig | Emergency override only | Security incidents, catastrophic events, demonstrated systemic collusion — publicly disclosed |

The Incubation Board is a funder and quarterly report recipient, not a governance tier.

## Build timeline for the node network

| Phase | Duration | Work |
|---|---|---|
| Contract finalization | ~2 weeks | Implement tier structure, work tracking, stake mechanics, slashing logic across the 5 remaining contracts (Token_v2 already complete) |
| Rust node implementation | ~3–4 weeks | Build operator software, validation logic, RPC client, attestation submission |
| Initial operator onboarding | M5/M6 milestones | Vetted operators come online during mainnet launch sequence |

## Key technical risks

See [10 — Risks & Security](./10-risks-security.md) for the full risk register. Headline technical risks specific to the product:

- **Audit finds material issues.** Expected and budgeted for via the M1 four-tranche structure.
- **Constellation pattern refactor on five remaining contracts.** Token v2 demonstrates the pattern works; remaining work is application, not invention.
- **Game result manipulation.** Mitigated via server-side validation, signed results, replay protection, and N-of-M operator attestation.

---

**Read next:** [05 — Validation & Traction](./05-validation-traction.md) → the real data on who's using the site today.
