# 07 — Business Model & Pricing

## How QZN makes money — in plain numbers

### Per-match routing (standard match, fixed in `constexpr`)

For every 100 QU of match value:

| Goes to                  | Amount     |
| ------------------------ | ---------- |
| Winner                   | 70 QU      |
| Protocol fee accumulator | 20 QU      |
| Immediate QU burn        | 5 QU       |
| Node operator            | 5 QU       |
| **Total**                | **100 QU** |

The 20 QU goes into the protocol fee accumulator. At every `BEGIN_EPOCH`, the accumulator empties through six streams.

### Where the accumulated 20 QU goes (off-pulse baseline)

| Stream                          | % of accumulator | Per 100 QU match |
| ------------------------------- | ---------------- | ---------------- |
| Operations                      | 5%               | 1 QU             |
| Reserve                         | 5%               | 1 QU             |
| Grants (builder fund)           | 10%              | 2 QU             |
| Dividends (to SC-share holders) | 30%              | 6 QU             |
| Burn                            | 20% \*           | 4 QU             |
| Operator compensation           | 30% \*           | 6 QU             |
| **Total**                       | **100%**         | **20 QU**        |

\* Burn and operator compensation are **pulse-variable**. During a contract's pulse epoch, its SC-share holders vote the burn rate within a 15–30% envelope; the operator-compensation share absorbs the remainder (20–35%), so burn + operators always sums to 50% of the accumulator. The figures above are the off-pulse baseline (20% / 30%).

**Operations vs operator compensation:** Operations (5%) is the protocol team treasury — development runway, infrastructure, and ongoing maintenance. Operator compensation (30%) is the separate work-based pool paid to the third-party node operators that host matches and maintain uptime. The two are distinct streams.

### Effective economics per standard match (off-pulse baseline)

| Stakeholder                          | Per 100 QU of match value |
| ------------------------------------ | ------------------------- |
| Winner                               | 70 QU (70%)               |
| QU burn (immediate 5 + accumulator 4)| 9 QU (9%)                 |
| Node operator (per match)            | 5 QU (5%)                 |
| Operator pool (per epoch)            | 6 QU (6%)                 |
| SC-share dividend pool               | 6 QU (6%)                 |
| Operations + reserve + grants        | 4 QU (4%)                 |
| **Total**                            | **100 QU**                |

**That is the protocol revenue model in one table.** Not "TVL" or "GMV" — actual QU flowing on-chain per match, split deterministically by contract code.

## Why this pricing metric fits the delivered value

The 20% accumulator share is the platform fee for providing match infrastructure: signed result validation, on-chain settlement, leaderboards, tournament hosting, builder routing. 20% is meaningfully lower than:

- Steam's 30% platform fee
- Mobile app store fees (30% standard, 15% for some categories)
- Traditional payment processor fees compounded with platform fees

And the 20% is split across multiple streams — 6 QU to operator compensation, 6 QU to SC-share dividends, 4 QU to burn, 2 QU to builder grants, and 1 QU each to operations and reserve. The protocol doesn't keep the 20% as profit; it distributes it through deterministic streams that pay operators for work, fund the ecosystem, and create durable burn.

**The pricing matches the value:** match validation work isn't free (operators do real labor, hence the per-match node payment and the operator pool); the platform provides leaderboards, tournaments, and builder distribution (justifying the 20% accumulator share); SC-share holders receive a dividend stream under Qubic's native smart-contract shareholder model.

## Where Incubation gets paid from

The 7.5% revenue share to Incubation (Component A) comes from **the reserve stream (5% of flush) plus half of operations (2.5% of flush)** = 7.5% of every accumulator flush.

**This does not touch the dividend stream (SC-share holders), the operator stream, or the burn stream.** It comes from operational buckets specifically. See [08 — Return to Incubation](https://github.com/dutt9145/qzn-incubation-proposal/blob/main/docs/08-return-to-incubation.md) for the full return mechanism detail.

### Worked example: 10,000 matches per month at average 1,000 QU per match

- Total match volume: 10,000,000 QU/month
- Accumulator fills: 2,000,000 QU/month (20%)
- Component A to Incubation: 150,000 QU/month (7.5% of accumulator)
- Annual run-rate to Incubation: ~1.8M QU
- Time to hit 10B cap at this rate: ~5,500 years

**Reality:** at small scale we won't hit the cap; we'll hit the 36-month sunset. At sustained bull-case scale (1M matches/month), annual run-rate approaches 180M QU and 36-month total approaches 540M QU — meaningful but still well below the cap. The cap exists as a realistic ceiling for breakout adoption scenarios; the sunset protects QZN against indefinite obligation at any scale.

---

# Tokenomics

## Total supply: 250,000,000 QZN (fixed)

| Allocation                           | Tokens          | % of supply |
| ------------------------------------ | --------------- | ----------- |
| ICO Phase 1                          | 10,000,000      | 4.0%        |
| ICO Phase 2                          | 25,000,000      | 10.0%       |
| ICO Phase 3                          | 15,000,000      | 6.0%        |
| QSWAP LP seed                        | 10,000,000      | 4.0%        |
| Team                                 | 20,000,000      | 8.0%        |
| Ecosystem                            | 50,000,000      | 20.0%       |
| Builder fund                         | 53,500,000      | 21.4%       |
| Treasury                             | 51,500,000      | 20.6%       |
| **Incubation Program (Component B)** | **15,000,000**  | **6.0%**    |
| **Total**                            | **250,000,000** | **100%**    |

### Notes on the allocation

- **Team allocation is intentionally restrained at 8%.** The founder has elected to keep team allocation smaller than typical for early-stage protocols and direct the difference toward the Builder fund and Treasury, where supply can be deployed to ecosystem participants and protocol operations.
- **Contractor and future-hire compensation** will be sourced from either Treasury or Team allocation based on the role, with allocation decisions discussed transparently with the community before commitment.
- **Incubation Program allocation is its own line item**, not nested under Treasury. The 15M QZN is committed to the Incubation Board as Component B (see [08 — Return to Incubation](https://github.com/dutt9145/qzn-incubation-proposal/blob/main/docs/08-return-to-incubation.md)) and is reserved before any other distribution from the protocol's allocation pool.
- **The Builder fund and the grants stream are one purpose.** The Builder fund allocation above is the token reserve granted to third-party builders to build on QZN; the 10% grants stream in the routing table (the "Grants (builder fund)" line) is the ongoing protocol-revenue top-up to that same builder-funding pool. If early builder demand outruns the seed, it can be supplemented from ICO proceeds.

## Vesting

| Bucket                | Vesting                               |
| --------------------- | ------------------------------------- |
| ICO purchasers        | Per-phase at purchase                 |
| LP seed               | Immediate (locked in QSWAP)           |
| Team                  | 6-month cliff + 30-month linear vest  |
| Ecosystem             | Gradual release per epoch             |
| Builder fund          | No vesting (released per-epoch as builder grants) |
| Treasury              | No vesting (multi-sig is the control) |
| Incubation allocation | 36-month linear vest, no cliff        |

## ICO mechanics (separate from this grant)

ICO will target 40B QU across three phases (5B / 20B / 15B at three price points) post-mainnet. 25% of proceeds burn at ICO close. ICO proceeds fund post-launch operations, builder fund seeding, treasury reserve, and ongoing development.

**The ICO does not repay the Incubation grant.** Repayment comes from protocol revenue (Component A) and the token allocation (Component B), not from token sale proceeds.

ICO timing and structure are designed to occur post-audit and post-mainnet — token purchasers buy into a working, audited protocol, not into a promise.

---

**Read next:** [08 — Return to Incubation](https://github.com/dutt9145/qzn-incubation-proposal/blob/main/docs/08-return-to-incubation.md) → the full return mechanism for the Incubation Board.