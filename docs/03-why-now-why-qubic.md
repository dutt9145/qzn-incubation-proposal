# 03 — Why Now, Why Qubic

## Why Qubic specifically

### Feeless settlement is the core enabler

QZN's per-match routing pays 70% to the winner, 20% to the protocol fee accumulator, 5% to immediate burn, and 5% to node operators. On a chain with gas fees, that 100% gets eaten before it reaches anyone. **Qubic is feeless — that's the only place this works.**

The math is not subtle. On Ethereum mainnet, a single ERC-20 transfer can cost more than the value of an entire QZN match settlement. On Solana, fees are lower but still non-zero, and reliability under load becomes a risk factor. On Qubic, every match settles for zero gas cost regardless of network conditions, and the deterministic block time means settlement timing is predictable.

### The SC-share-record primitive

Qubic lets a contract emit chain-native records that receive programmed dividend distributions from contract activity. No other chain has this cleanly. Without it we'd have to issue a registered security or build a custom dividend mechanism that creates regulatory exposure. Qubic gives us the primitive for free.

This is structurally important for QZN's long-term holder alignment. SC-share-record holders receive 55% of the accumulator flush as programmed dividends — meaning long-term participants benefit from match volume without QZN needing to operate a securities-grade distribution program. The dividend mechanism is on-chain, deterministic, and bounded by smart contract code.

### Qubic Oracle Machines for randomness

Qubic's Oracle Machine infrastructure (launched February 2026) provides verifiable randomness validated through the same Computor consensus that secures the network itself. QZN integrates with this for tournament bracket seeding, random validator assignment in the node network, match-result tiebreakers, and randomness exposed to builder-published games.

This is meaningfully better than building a custom randomness smart contract (RANDOM). Smart contract randomness is notoriously difficult to do correctly; outsourcing to Qubic's consensus-validated oracle infrastructure removes a class of attack surface entirely. See [04 — Product & Demo](./04-product-demo.md) for how oracle randomness integrates with the node architecture.

## Why now

Three things are true today that weren't true twelve months ago:

### 1. The code is ready

QZN_Token (Slot 0) refactor is complete with 50/50 procedure tests green. The constellation pattern application to the remaining five contracts (RewardRouter, GameCabinet, Nodes, TournamentEngine, TreasuryVault) is scoped under M2 — roughly two weeks of focused engineering. Token v2 demonstrates that the pattern works; the remaining contracts apply the same proven structure.

### 2. The ecosystem is ready

QSWAP, PORTAL, QIP, and Qusino exist as usable ecosystem infrastructure. QZN doesn't need to bootstrap a DEX, a liquidity infrastructure, an SC-share-record framework, or a casino-mechanics reference implementation. Each of those exists already, built by other Qubic-native teams. QZN integrates with them rather than rebuilding them.

The ecosystem also has Qubic Oracle Machines live on mainnet, which QZN uses for randomness rather than building custom. This is a year-recent infrastructure capability that wasn't available twelve months ago.

### 3. The founder is ready

Twelve months of solo build work has produced a working product (three games at qzn.app, 1,800 unique visitors in the past 30 days from 58 countries), six deployed contracts, the constellation architecture refactor, and the team and counsel relationships necessary to ship. Travel-contract MLS work provides current operational runway through summer 2026; the focus and bandwidth exist now in a way that may not persist indefinitely.

## The audit is the gate

The protocol code is built. The frontend is built. The backend is operational. The games are live. The constellation pattern is proven in Token v2. The five-contract refactor is scoped, and the Rust node implementation is planned for the following 3–4 weeks.

What's blocking mainnet is the external audit. mundus_tj85 has quoted 20B QU for the full six-contract scope. Without that audit, QZN cannot responsibly launch with users' real money flowing through the contracts. With it, every other deliverable becomes execution work the founder can complete.

**The cost of the audit doesn't go down if we wait.** Delaying the proposal does not reduce audit cost or de-risk the project. It just delays the validation step that everything else depends on.

---

**Read next:** [04 — Product & Demo](./04-product-demo.md) → what's live today and the full technical architecture.
