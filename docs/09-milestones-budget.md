# 09 — Milestones & Budget

## Overview

| Milestone | Tranche | Focus |
|---|---:|---|
| **M1** | **20.0B** | **Audit — paid in four 5B tranches to mundus_tj85** |
| M2 | 0.5B | Mechanics + multi-sig finalization, spec/terminology publication (contract refactor already complete) |
| M3 | 1.0B | Arcade production-ready |
| M4 | 0.5B | Builder portal (no fund seed — that's from ICO) |
| M5 | 1.5B | Token integration on mainnet + counsel + ICO prep |
| M6 | 1.5B | Launch + first quarter operations |
| **Total** | **25.0B** | |

Timeline: ~12 months from M1 acceptance through mainnet launch.

## M1 — Audit (20B, four tranches)

| Tranche | Amount | Trigger | Pays for |
|---|---:|---|---|
| **M1.T1** | 5.0B | Audit kickoff | Scope agreement, contract handoff, initial review begins |
| **M1.T2** | 5.0B | Initial findings delivered | Vulnerability report to QZN and Board |
| **M1.T3** | 5.0B | Remediation review | Mundus confirms fixes hold |
| **M1.T4** | 5.0B | Final sign-off | Final audit report (summary public, full to Board) |

### Why 20B and why mundus_tj85

Mundus is currently the only practical option for auditing Qubic-native C++ smart contracts at this complexity. We did not solicit competing bids because the audit market for Qubic-native code is small and Mundus is the established practitioner. The 20B figure represents Mundus's quote for the full six-contract scope at projected QU pricing. **If the Board has a different auditor preference or wants us to seek competing bids, we will do so before M1 begins.**

The four-tranche structure gives the Board four decision points. If T1 findings reveal a catastrophic architectural issue, the Board declines T2–T4 and exposure caps at 5B (20% of the 25B grant). This is the Board's primary risk mechanism.

### M1 acceptance criteria

- Audit engagement letter signed by Mundus with milestone-tranche structure
- Pre-audit code remediation complete (constellation refactor, known internal findings)
- All six contracts in audit-ready state at testnet
- Final audit report delivered (summary public, full to Board)
- All audit findings either remediated or formally accepted by Board with reasoning

## M2 — Mechanics + multi-sig (0.5B)

**Acceptance criteria:**

- BPS routing spec locked and published
- Tokenomics spec locked and published
- Three-layer terminology framework published
- Multi-sig operational (Key 1 founder, Key 2 Spike) with documented disbursement procedures
- Pre-audit remediation of known internal-audit findings complete
- Constellation pattern applied to all six contracts with 406 procedure and invariant tests passing (completed ahead of the grant)
- `QZN_Nodes` refactored to work-based attribution model (completed ahead of the grant)
- Founder conflict-of-interest policy published
- Light counsel engagement initiated (David Hoppe + Aaron Hall scoped)

**Use of funds:** founder operational support, counsel engagement deposits, multi-sig setup costs, spec/terminology documentation and publication.

## M3 — Arcade production-ready (1.0B)

**Acceptance criteria:**

- snaQe, paQman, TANQ-Battle polished to production quality
- XP system + leaderboard fully operational
- Frontend production-grade (performance optimized, mobile responsive, accessibility baseline)
- Backend (Railway + Supabase) on production-tier monitoring
- Infrastructure load-tested for tournament-scale traffic spikes (10x normal volume)
- Public bug bounty program launched

**Use of funds:** infrastructure scaling (Railway + Supabase production tiers), founder operational support, design refinement, security tooling, bug bounty program seed.

## M4 — Builder portal (0.5B)

**Acceptance criteria:**

- Builder portal UI live (account creation, game metadata, parameter configuration, publishing flow)
- Draft/published/archived state machine operational
- On-chain registration for published games via `QZN_GameCabinet`
- Builder documentation published (technical integration guide, economics explainer)
- 3–5 third-party builders onboarded as proof points
- Pham (existing frontend contributor) formalized as reference case

**Use of funds:** founder operational support, documentation production, modest support for early builder onboarding (technical assistance, not token grants — Builder Fund seed comes from ICO proceeds, not this grant).

## M5 — Token integration + counsel + ICO prep (1.5B)

**Acceptance criteria:**

- QZN utility token integrated across all six contracts on mainnet
- Gameplay/tournament/publishing utility live and tested
- Tokenomics published with full disclosures
- QSWAP liquidity pair prepared (coordination with Spike)
- Counsel sign-off package complete (David Hoppe securities review, Aaron Hall LLC review)
- ICO mechanics documented and published
- Three-phase ICO infrastructure ready for launch

**Use of funds:** counsel fees (Hoppe + Hall), founder operational support, ICO infrastructure setup, QSWAP integration costs, documentation production.

## M6 — Launch + first quarter ops (1.5B)

**Acceptance criteria:**

- Mainnet launch event executed
- Launch tournament with prize pool operational
- QSWAP pair seeded (combined ICO + partial M6 contribution)
- First quarterly Incubation report published with on-chain numbers
- Builder grants pilot operational (funded from Builder Fund, not grant)
- First three months of post-launch operations funded
- Node operator network operational with vetted Genesis-tier operators online

**Use of funds:** launch event costs, tournament prize pool seed, founder operational support, first-quarter infrastructure costs, quarterly report production.

## Decline points (Board risk management)

| Decline at | Cumulative paid | % of total | Scenario |
|---|---:|---:|---|
| Decline M1.T2 (after T1 = catastrophic finding) | 5.0B | 20.0% | Audit reveals architectural issues |
| Decline M1.T3 (after T2) | 10.0B | 40.0% | Findings deemed unfixable |
| Decline M1.T4 (after T3) | 15.0B | 60.0% | Remediation fails verification |
| Decline M2 (audit complete) | 20.0B | 80.0% | Despite clean audit, decision not to proceed |
| Decline M3 | 20.5B | 82.0% | Refactor delivered but not production-ready |
| Decline M4 | 21.5B | 86.0% | Production arcade delivered but builder portal scope abandoned |
| Decline M5 | 22.0B | 88.0% | Builder portal delivered but token integration abandoned |
| Decline M6 | 23.5B | 94.0% | Token integration delivered but launch scope abandoned |

## Funding discipline (commitment)

- Grant does not pay founder salary directly. Founder operational support refers to specific deliverable-tied costs (audit kickoff coordination, documentation production, infrastructure costs the LLC pays on QZN's behalf), not direct salary draws.
- Grant does not buy founder personal SC-share holdings
- All funding flows through Qubzylthar Nexus LLC and the QZN multi-sig
- Unused tranches roll forward, not redirected to other categories
- Final accounting published at M6 by milestone and by spending category
- Quarterly reports include cumulative spend against tranche budgets

## One-year commitment

Per Incubation Program requirements, I commit to a full 12-month delivery and maintenance period through mainnet launch and the first post-launch quarterly Incubation report. The 12-month window covers M1 audit (~3–4 months), M2–M5 build and integration (~6–7 months), and M6 launch + first quarter operations (~3 months). Beyond the 12-month commitment, QZN continues as ongoing protocol operation with Component A quarterly payments through the 36-month sunset.

---

**Read next:** [10 — Risks & Security](./10-risks-security.md) → security assumptions, audit plan, operational risks, and disclosures.