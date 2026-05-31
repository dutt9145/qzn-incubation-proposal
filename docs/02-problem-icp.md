# 02 — Problem & ICP

## The problem we solve

Qubic has infrastructure. It does not have many consumer products a non-crypto person can use in two minutes. That's the gap QZN fills.

More specifically: there is no consumer-grade entry point to Qubic that demonstrates the chain's feeless, high-throughput characteristics through a familiar interaction pattern. New users discovering Qubic encounter validators, smart contracts, IPOs, mining pools — all interesting to technical participants, none of which is "open this URL and have fun in 30 seconds."

## Who we serve (ICP)

QZN has two distinct user profiles, both important:

### Primary: Curious crypto-adjacent gamers

People who have heard of crypto but aren't deeply technical. They want to try Web3 without setting up a wallet first, without paying gas fees to see if a game is fun, without reading documentation. Their pain today:

- **Most Web3 games gate gameplay behind wallet setup.** Friction before fun = abandonment.
- **Gas fees per move or per match are absurd** on chains that charge them. A casual gamer is not going to pay $0.50 per match.
- **Existing Web3 game economies are extractive** — designed to convert players into token buyers, not to be fun first. Players notice.

### Secondary: Game builders looking for distribution

Independent game developers who want their work distributed without taking on the full burden of platform infrastructure (matchmaking, leaderboards, settlement, payments). Their pain today:

- **Building distribution infrastructure is expensive.** Most indie devs don't want to build a payments stack or run their own settlement.
- **Existing Web3 publishing platforms either don't exist or are heavily extractive.**
- **Traditional gaming platforms (Steam, mobile app stores) take 30%+ of revenue** and have heavy curation gates.

## How they solve it today

### For gamers

| Current solution | Why it's insufficient |
|---|---|
| Traditional free-to-play games (mobile, browser) | Not Web3, no token ownership, no on-chain identity, no settlement |
| Existing Web3 games on EVM chains | Gas fees per action, wallet setup friction, often extractive economies |
| NFT-based games | High entry cost, speculative dynamics, often not fun as games |
| Crypto-curious players who give up | They don't enter the space at all |

### For builders

| Current solution | Why it's insufficient |
|---|---|
| Build own platform from scratch | Months of infrastructure work before shipping any game |
| Publish on existing Web3 platforms | Where? Most Web3 game platforms have limited reach or are themselves struggling for users |
| Publish on traditional platforms (Steam, mobile stores) | 30% revenue share, slow approval, no on-chain settlement |
| Stay out of Web3 entirely | The most common choice — but Web3 game distribution remains an unsolved opportunity |

## Why current alternatives are structurally insufficient

The core issue is that **Web3 gaming on chains with gas fees cannot escape extraction dynamics.** When every action costs gas, game design pressure pushes toward token-mediated mechanics that justify the fees — which produces games that feel like trading platforms with a thin gameplay skin.

Qubic's feeless model removes that pressure. QZN can route 70% of match value to the winner because there is no gas charge eating the routing. The protocol fee accumulator (20%) feeds dividends, operator compensation, burn, builder grants, operations, and reserve — all without making the player pay per move.

The SC-share-record primitive then enables programmed dividends to long-term holders without requiring the protocol to issue a security. No other chain has this primitive cleanly. Without it, QZN would either need to issue a registered security (regulatory exposure for a solo founder) or skip the dividend mechanism entirely (weakening the long-term holder alignment).

## Why QZN can serve both audiences at once

Gamers and builders are not separate markets that we serve in parallel — they're a two-sided ecosystem that compounds. Builders bring games; games attract players; players generate match volume; match volume generates revenue routed to builders. The Builder Fund (53.5M QZN, 21.4% of supply, plus accumulated revenue stream) underwrites the builder side until volume can sustain it organically.

This is the standard arcade/publishing-platform model, applied to a chain where the per-match economics actually work.

---

**Read next:** [03 — Why Now, Why Qubic](./03-why-now-why-qubic.md) → why this should exist now and why Qubic is the only place where the math works.