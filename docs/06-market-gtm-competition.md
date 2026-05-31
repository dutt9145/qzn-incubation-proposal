# 06 — Market, GTM, Competition

> **Note on this section:** This is the section of the proposal where existing material was thinnest, so it has been built out from first principles. Numbers presented are bottom-up estimates with stated assumptions, not citations of third-party reports. The Board should treat this section as honest reasoning under uncertainty rather than as validated market research.

## Bottom-up market logic

### The two-sided market

QZN serves two distinct user groups whose growth compounds:

- **Players** generate match volume, which generates protocol revenue
- **Builders** publish games, which expands what players can play
- More players make builders' games more economically attractive
- More builder games gives players more reasons to return

The flywheel is standard for arcade and publishing platforms. Steam, Roblox, and Itch.io all run variants of this pattern. QZN's specific contribution is to make the per-match settlement math work — feeless settlement is what allows the protocol to route 70% of match value to winners while still supporting builder revenue and ongoing operations.

### Player-side bottom-up estimate

Working from what we know rather than top-down market reports:

**Year 1 target (post-launch):** 500–2,000 monthly active wallets, 5,000–25,000 matches/month total volume.

How we get there:
- Pre-launch organic baseline today: 1,800 unique visitors / 6,170 visits in 30 days, zero acquisition spend
- Roughly 10–20% of those visitors become return players post-launch (when there's actual on-chain settlement worth coming back for): ~180–360 monthly active wallets from existing audience
- Qubic Discord and Telegram community: estimated 5,000–10,000 active members across channels; if 3–5% of that audience tries QZN in Q1, that's another ~150–500 wallets
- Cross-promotion with QIP, Qusino, QSWAP, and PORTAL communities adds incremental: ~100–300 wallets
- Combined first-year-realistic range: ~430–1,160 monthly active wallets

This is conservative. It does not assume any successful paid acquisition, viral content, or breakout tournament moment. Those are upside.

**Year 3 target:** 5,000–25,000 monthly active wallets if the builder portal scales and a small handful of breakout builder games emerge.

### Builder-side bottom-up estimate

**M4 target:** 3–5 third-party builders onboarded as proof points.

**Year 1 post-launch target:** 10–25 published builder games.

How we get there:
- Hunter knows several Qubic-ecosystem developers personally
- Builder Fund (53.5M QZN allocation) provides direct economic incentive for early publishers
- 5% builder revenue stream from accumulator flush plus per-game customization of routing creates ongoing builder economics
- Pham (existing frontend contributor) becomes a reference case for "what a builder publishing on QZN looks like"

**Year 3 target:** 50–200 published builder games if the platform reaches sustainable economics.

### Revenue bottom-up

Per [07 — Business Model & Pricing](./07-business-model-pricing.md), each 100 QU of match value routes 20 QU to the accumulator. The accumulator then flushes through six streams at epoch boundaries. Total annual protocol revenue is fundamentally a function of match volume × average match value.

**Conservative Year 1 estimate:** 5,000 matches/month × 1,000 QU/match × 12 months × 20% accumulator share = **12M QU/year in accumulator flow.** Distributed across operations (0.6M), reserve (0.6M), grants (1.2M), dividends (3.6M), burn (2.4M), and operator compensation (3.6M).

**Base case Year 1:** 15,000 matches/month × 1,000 QU/match × 12 months × 20% = **36M QU/year.**

**Bull case Year 1:** 50,000 matches/month × 1,500 QU/match × 12 months × 20% = **180M QU/year.**

These numbers scale roughly linearly with match volume and roughly linearly with average match value.

## Alternatives — what users would use otherwise

### For players choosing where to play

| Alternative | What it offers | Why it doesn't kill QZN |
|---|---|---|
| Traditional free-to-play games (mobile, browser) | Polished gameplay, large libraries | No Web3 ownership, no on-chain identity, no settlement — different value proposition |
| Web3 games on Ethereum L2s (Polygon, Arbitrum) | Token ownership, large user pool | Gas fees per action, extractive economy designs, fragmentation across multiple chains |
| Solana-based gaming (e.g., Star Atlas, MagicEden) | Lower fees than mainnet Ethereum | Still has fees, congestion at peak demand, limited dividend primitive for long-term holders |
| Other Qubic consumer apps | Same chain, ecosystem alignment | We don't compete with Qubic's existing apps — we add a new category (arcade games), not a duplicate of existing ones |
| Stay outside Web3 entirely | No friction at all | This is the largest "competitor" — most casual gamers are not in Web3. QZN's job is to make Web3 worth the (small) friction. |

### For builders choosing where to publish

| Alternative | What it offers | Why it doesn't kill QZN |
|---|---|---|
| Steam | Massive user base, mature publishing tools | 30% revenue share, slow approval, no on-chain settlement, no token economy |
| Mobile app stores (iOS, Google Play) | Massive user base, in-app purchase infrastructure | 30% revenue share, mobile-only, no Web3 native features |
| Web3 game platforms (existing) | On-chain settlement, token integration | Most have struggled to retain users; small platforms can't compete on distribution |
| Self-publish (own website, own infrastructure) | No platform fees, full control | Need to build everything yourself; no built-in player base; no built-in payment routing |
| Stay out of gaming, build other apps | Many other things to build | The opportunity cost question — but QZN's specific bet is that gaming is an underserved Qubic application category |

## Buyer vs. user distinction

For QZN's main user flow, **buyer and user are the same person.** A player who plays snaQe is the same person who pays to enter a tournament or buys QZN tokens for utility purposes. There is no enterprise-procurement layer.

For the builder side, the **builder is the buyer**, and **the builder's game's players are the users**. Builders pay (in time/effort/QZN for premium features) to publish; players pay (in match entry fees, tournament fees) to engage. The two flows are linked through the accumulator and the Builder Fund.

## Acquisition channels

### Pre-launch (current)

Organic only. 1,800 unique visitors over 30 days from 58 countries with zero acquisition spend. Discovery happens through:
- Qubic Discord and Telegram cross-references
- Direct sharing by community members
- Founder posts in Qubic ecosystem channels
- Inbound from Qubic Ambassador activity

### Post-launch (planned)

| Phase | Audience | How |
|---|---|---|
| First 100 | Qubic ecosystem | Discord/Telegram via our existing marketing bot, AMA announcements, ecosystem cross-promo |
| First 1,000 | Web3 gaming aggregators | Listings on aggregator sites (DappRadar, PlayToEarn, others), Web3 gaming Twitter, Qubic ecosystem amplification |
| First 10,000 | Casual gamers + builders | Paid acquisition (modest budget post-revenue), influencer partnerships, builder-driven traffic |
| Long-term | Game builders | Builder portal as primary acquisition surface — quality builder games attract their own audience |

Each phase is gated on M4, M5, M6 deliverables from [09 — Milestones & Budget](./09-milestones-budget.md).

## Competition — direct comparable analysis

There is no direct competitor that does exactly what QZN does (Qubic-native, feeless, six-contract Constellation architecture, builder portal). The relevant comparison frame is:

### Web3 arcade-style platforms broadly

Many have launched; few have sustained traction. The pattern of failure has been:
- **Extractive token economies** that drive away players
- **Gas-fee friction** that breaks per-match economics
- **No builder economics** so the platform owner has to provide all content
- **Poor distribution** because Web3 game discovery remains broken

QZN's structural answers to each:
- Routing pays 70% to winners; protocol revenue comes from a 20% accumulator that funds platform without being extractive at the individual-match level
- Qubic is feeless
- Builder Fund + 5% builder revenue routing creates real builder economics
- Distribution remains an unsolved problem broadly, but Qubic ecosystem cross-promotion + builder-driven traffic + word of mouth from a good product are the realistic path

### Other Qubic-native consumer products

The closest comparables are Qusino (casino mechanics) and QIP (interest products) — both ecosystem-native projects. They're not direct competitors; they're complementary surfaces in the Qubic consumer-app landscape. QZN expects collaboration with QIP/Qusino communities, not competition.

## Why QZN can win (or at least survive long enough to find out)

The defensible positioning is:

1. **Qubic is the only chain where per-match economics work without extraction.** That's not a competitive moat against future feeless chains, but it's a real structural advantage today.
2. **The builder portal creates platform value that compounds.** Every builder game is content QZN didn't have to build. Two-sided platforms with working economics are durable.
3. **The Constellation architecture means governance is bounded.** No founder discretion to dilute holders or change routing arbitrarily. That's credibility.
4. **Three live games + 58 countries of organic interest** is real evidence of demand, even if modest.

## What we don't claim

- We do not claim a verified TAM. Bottom-up estimates above are reasoning, not validation.
- We do not claim guaranteed Year 1 numbers. The targets in the bottom-up section are ranges, not promises.
- We do not claim to have figured out distribution. Web3 game distribution is unsolved generally; QZN's plan is to chip at it incrementally with the channels listed above.
- We do not claim to be the only thing that could possibly work. We claim to be a reasonable bet for the Qubic ecosystem to make given the structural advantages above and the modest existing evidence.

---

**Read next:** [07 — Business Model & Pricing](./07-business-model-pricing.md) → how QZN makes money and the tokenomics.