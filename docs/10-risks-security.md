# 10 — Risks & Security

## Risk overview

QZN's risks fall into five categories: technical, product, legal/regulatory, operational, and key-person. Each is named honestly below, with mitigations. The legal/regulatory section includes the full three-layer structural separation and disclosure policy.

## Technical risks

| Risk | Mitigation |
|---|---|
| Audit finds material issues | Expected. M1 four-tranche structure is the mitigation. Board declines if findings are unfixable. |
| Constellation pulse rotation edge case | Bounded by 15–30% vote envelope. Deterministic logic. 406 procedure and invariant tests passing across all six contracts. |
| Game result manipulation | Server-side validation, signed results, replay protection, tournament review, N-of-M operator attestation requirement. |
| Oracle integration failure or compromise | QZN integrates with Qubic Oracle Machines (validated through Computor consensus). Compromise of Qubic oracles would affect the entire Qubic ecosystem, not QZN specifically. Application-level fallback paths defined for tournament continuation if oracle unavailability is detected. |

### Internal-audit findings remediated before mundus_tj85's external review

- **Constellation pattern applied to all six contracts** — `RewardRouter`, `GameCabinet`, `Nodes`, `TournamentEngine`, and `TreasuryVault` now carry the same procedure/invariant test treatment as `QZN_Token`; 406 tests passing across the suite (complete)
- **`epochEfficiencyRating` legacy multiplier path** — removed during the `QZN_Nodes` refactor to the work-based attribution model (complete)
- **`QZN_Nodes` architectural refactor** — stake-tier-multiplier prototype replaced with work-tracking attribution, proportional epoch payouts, and slashing logic (complete)
- Smaller findings grouped into the same pre-audit pass

These are disclosed to counsel and will be disclosed to Mundus at audit kickoff. **Not concealed.**

## Audit plan

| Phase | Activity | Timeline |
|---|---|---|
| Pre-audit remediation | Constellation refactor + known findings — complete | Done (ahead of M1) |
| Audit kickoff (M1.T1) | Scope agreement, contract handoff to Mundus | Triggered by M1 approval |
| Initial findings (M1.T2) | Mundus delivers vulnerability report | ~4–6 weeks after kickoff |
| Remediation (between T2 and T3) | QZN addresses findings; Mundus verifies | ~2–4 weeks |
| Remediation review (M1.T3) | Mundus confirms fixes hold | Trigger for T3 payment |
| Final sign-off (M1.T4) | Final audit report (summary public, full to Board) | Trigger for T4 payment |

If the Board has a different preferred auditor or wants QZN to solicit competing bids, we will do so before M1 begins.

## Product risks

| Risk | Mitigation |
|---|---|
| Low retention post-launch | Arcade structure (multiple games + builder content), XP/tournament loops, ongoing game refinement |
| Builder portal sees no adoption | M4 includes 3–5 proof-point builders as gating deliverable; failure here re-scopes M5/M6 |
| Launch tournament flops | Pre-coordination with Qubic ecosystem partners; sized prize pool; broad invitation across QIP/Qusino/QSWAP/PORTAL communities |
| Single-region traffic dependency | Current data shows 58 countries; not regionally concentrated. Post-launch acquisition plans diversify further. |

## Legal & regulatory risks

| Risk | Mitigation |
|---|---|
| QZN token misconstrued as investment | Three-layer separation (below); utility documentation; marketing language standard |
| SC-share records misconstrued as company shares | Clear terminology throughout; tokenomics fully published |
| Founder personal holdings create conflict | Personal portfolio funds only; multi-sig prevents self-dealing; no MNPI trading commitment (full policy below) |
| Regulatory action on tokens with economic mechanics | Three-layer separation; counsel review (David Hoppe for securities, Aaron Hall for LLC); engagement being scoped |
| Jurisdictional differences in token treatment | Counsel review of geographic distribution; potential geoblocking infrastructure post-launch if required |

### The three-layer structure

| Layer | What it is | What it is NOT |
|---|---|---|
| **Qubzylthar Nexus LLC** | Wyoming LLC. Owns qzn.app, frontend, backend, off-chain revenue, IP. | Not the token. Not the protocol. |
| **QZN utility token** | 250M fixed supply, Qubic-native. Gameplay, tournaments, publishing, settlement. | Not LLC equity. Not a security claim. No dividends. No claim on off-chain revenue. |
| **SC-share records** | Qubic-native primitive. Programmed dividends from accumulator flushes (30% dividends stream). | Not LLC shares. Not QZN tokens. Not off-chain revenue claims. |

**The three layers do not commingle.** Funds flowing in one layer do not flow to another except through the documented routing mechanisms specified in the smart contract code.

### Terminology standard (what we use and what we don't)

| ✗ Avoid | ✓ Use |
|---|---|
| QZN shareholders | QZN token holders / SC-share-record holders |
| Passive income | Programmed Qubic-native contract-level dividends |
| Investment upside | Protocol utility |
| Price support | Orderly access liquidity for protocol utility |
| Company shares | SC-share records |
| Profit rights | Contract-level dividend mechanics |

The Discord marketing bot, all user-facing documentation, AMAs, and founder communications follow this standard.

### What QZN token does / does not provide

**Provides:** gameplay access, tournament entry, game publishing rights, settlement utility, protocol interactions.

**Does NOT provide:** LLC equity, dividends, passive income, off-chain revenue share, liquidation rights, redemption rights, voting on LLC operations, claims on LLC treasury or assets.

### What SC-share records do / do not provide

**Provides:** programmed dividend stream from accumulator flushes (the 30% dividends stream off-pulse), distributed via `distributeDividends`.

**Does NOT provide:** LLC ownership, IP ownership, treasury claims, off-chain revenue claims, guaranteed dividend amounts, guaranteed liquidity, guaranteed resale value, LLC voting rights. Dividends may be zero in any epoch where match settlement activity is insufficient.

### Founder conflict-of-interest policy

The founder may hold personal positions in Qubic-ecosystem assets (this is the normal posture for an active participant in the ecosystem). These personal positions are subject to the following commitments:

- Funded only from personal portfolio funds — **never** from LLC funds, grant funds, customer funds, SAFE proceeds (no SAFE exists), or token-sale proceeds
- Personal wallets held separately from the QZN multi-sig treasury
- No transactions in QZN or QZN-related positions on the basis of material non-public information (audit results, major announcements, security events, token events, liquidity events)
- Multi-sig structure (Key 1 founder, Key 2 Spike) is the operational control preventing any self-dealing with grant funds or protocol treasury

**Personal asset disclosure is not provided** for safety and operational reasons (targeted attacks on disclosed wallets, social engineering surface, negotiating-position considerations). The Board has visibility into all QZN protocol-related economics through the tokenomics in [07 — Business Model & Pricing](./07-business-model-pricing.md), the multi-sig structure, the funding-discipline commitments in [09 — Milestones & Budget](./09-milestones-budget.md), and the quarterly Incubation reports.

If the Board has specific concerns about conflicts of interest that the structure above does not address, we will work with counsel (David Hoppe / Aaron Hall) on additional targeted disclosures that satisfy the Board's concern without creating safety exposure.

### XP, points, badges (pre-token)

Non-transferable platform records. Not tokens. Not money. Not securities. No guaranteed claim on future QZN allocation or future protocol value.

### Liquidity

QZN liquidity supports orderly access for gameplay, publishing, tournaments, and settlement. **Not** price stability. **Not** appreciation guarantee. **Not** downside protection.

## Operational risks

### Founder bandwidth / key-person risk

I am one person. All code is in version control accessible to multi-sig signers. Multi-sig prevents single-key treasury control. The risk is partially mitigated, not eliminated. If I become unavailable for an extended period, QZN does not have a deep bench.

**Honest assessment:** this is the single biggest risk to the proposal that the Board cannot fully de-risk via funding structure. Partial mitigations:

- All code in public version control at [github.com/dutt9145/qzn-core-lite](https://github.com/dutt9145/qzn-core-lite)
- Multi-sig structure means treasury can be operated by Key 2 holder (Spike) if Key 1 holder becomes unavailable
- JoeTom (Qubic core dev) has architectural knowledge of the protocol
- Documentation produced under M2 includes operational runbooks

The Board should weight this risk explicitly in approval decision. A solo-founder project is inherently more concentrated than a multi-person team.

### Infrastructure dependencies

| Dependency | Mitigation |
|---|---|
| Railway (backend hosting) | Multiple cloud provider options if needed; backend is portable Node.js |
| Supabase (database) | Standard PostgreSQL; portable to any Postgres provider |
| Cloudflare (CDN, DNS) | Standard CDN; portable to alternative providers |
| Qubic mainnet | Foundational dependency; any chain failure affects QZN equally to other Qubic projects |
| Qubic Oracle Machines | New infrastructure (Feb 2026); fallback paths defined for outages |
| mundus_tj85 (auditor) | Sole practical option for Qubic-native C++ audit; if relationship fails, audit timeline extends |

### Multi-sig key holders

| Key | Holder | Role |
|---|---|---|
| Key 1 | Founder (Hunter Duttenhefer) | Primary operational signer |
| Key 2 | Spike (QSWAP/PORTAL) | Secondary signer, independent of founder |

Both signers required for treasury disbursements. Multi-sig wallet address to be confirmed with Spike before Incubation submission.

## Security assumptions

QZN's security model rests on five assumptions, named here for the Board's evaluation:

1. **Qubic network consensus is secure.** If Qubic itself is compromised, QZN is compromised. This is true for all Qubic-native protocols.
2. **mundus_tj85's audit catches material vulnerabilities.** The four-tranche structure provides the Board with checkpoints; remediation review (T3) and final sign-off (T4) are explicit verification points.
3. **Operators do not collude at scale.** Mitigations described in [04 — Product & Demo](./04-product-demo.md) (N-of-M attestation, oracle-driven random assignment, public attestation history, slashing) make collusion expensive and detectable, but do not make it impossible.
4. **Founder + Key 2 multi-sig is honestly operated.** No structural mechanism prevents collusion between Key 1 and Key 2 holders. This is mitigated by public reporting commitments and the LLC's legal obligations under Wyoming corporate law.
5. **Backend infrastructure remains operational.** Hosting, database, and CDN failures would disrupt QZN's gameplay flow. Standard cloud reliability practices apply, but no protocol-level mitigation can replace operational uptime.

The Board should evaluate whether these assumptions are reasonable for the scale of grant being requested.

---

*End of proposal documents. Return to [README](../README.md) or [00 — Summary](./00-summary.md).*