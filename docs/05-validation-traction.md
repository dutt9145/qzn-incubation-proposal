# 05 — Validation & Traction

This is the section that got criticized in the last review. We rebuilt it around what we actually have.

## What 30 days of Cloudflare data shows (qzn.app, 26 April – 26 May 2026)

**1,800 unique visitors generating 6,170 total visits, from 58 countries. Zero acquisition spend.**

| Metric | Value |
|---|---:|
| Unique visitors | 1,800 |
| Total visits | 6,170 |
| Average sessions per visitor | ~3.4 |
| Total requests | 30,270 |
| **Countries with measurable traffic** | **58** |
| Top 10 country share of requests | ~88% |

The visits-to-visitor ratio of ~3.4 means a meaningful portion of visitors return across the 30-day window. 58 countries means the audience is genuinely global, not regionally concentrated — which is what you'd expect from organic discovery within the international Qubic community.

## Top 10 markets (88% of requests)

| Country | Requests | Bandwidth |
|---|---:|---:|
| United States | 11,460 | 160.76 MB |
| Netherlands | 8,730 | 54.64 MB |
| France | 5,040 | 40.35 MB |
| Singapore | 2,600 | 29.82 MB |
| Canada | 1,520 | 53.73 MB |
| Germany | 1,350 | 11.39 MB |
| Brazil | 915 | 12.99 MB |
| India | 814 | 2.16 MB |
| United Kingdom | 748 | 13.89 MB |
| Vietnam | 653 | 8.54 MB |

## The other 48 countries (12% of requests)

Notable presence beyond Top 10 includes Lithuania, Bulgaria, Hong Kong, China, Australia, Ireland, Italy, Russia, Poland, Indonesia, Belgium, Taiwan, Japan, Sweden, Romania, South Korea, Finland, Spain, Turkey, Israel, Czech Republic, Switzerland, and 26 additional countries with smaller volumes.

**This geographic distribution matches the geography of the Qubic community itself** — strong European and Asian presence alongside North American traffic, consistent with organic discovery via Discord, Telegram, and ecosystem cross-references. It does not match the patterns of paid-acquisition campaigns (which concentrate in single regions) or bot-farm origin (which concentrate in specific data-center geographies).

## What this data does and does not prove

**It does NOT prove product-market fit.** 60 daily unique visitors at pre-launch is not market fit. Most of those 58 countries had <500 requests over 30 days — that's interest, not adoption. We are not claiming it is.

**It does prove:**

- People who are not me are visiting the site voluntarily
- Traffic spans 58 countries, ruling out regional anomalies or single-source bot origin
- A meaningful portion of visitors return across the 30-day window
- We achieve this with no marketing budget, no paid acquisition, no SEO investment
- The geographic distribution matches expected organic-discovery patterns for Qubic-community origin

This is leading indicator, not market fit. **Market fit is what we measure post-mainnet launch under M6 with real on-chain match activity and quarterly Incubation reports.**

## Honest data limitations

- Cloudflare's free tier doesn't expose bot scores, so some portion of traffic may be crawlers or automation we can't filter
- Netherlands traffic is high relative to expected baseline; partially explained by European Qubic community activity and Cloudflare's own Amsterdam datacenter infrastructure
- Tor exit nodes appear at 7 requests over 30 days; this is normal for any public website and indicates privacy-preserving access channels are functional
- Daily trend is flat-to-slightly-declining after an early-period spike, not a growth pattern
- The long tail (48 countries, 12% of requests) is mostly single-digit request volumes — meaningful as a signal of breadth, not as evidence of those markets specifically
- We are reporting data as-is; no claims that all visitors are human or that the trajectory is upward

## Retention indicator

The 3.4 sessions-per-visitor ratio is the most useful retention signal we have at pre-launch. For comparison, typical pre-launch landing pages see 1.1–1.5 sessions per visitor (mostly one-and-done curiosity visits). 3.4× suggests a non-trivial portion of visitors come back to engage further — which is what an arcade product should produce. We don't have time-on-site or game-completion data at this stage; those will become available post-launch when on-chain match activity provides hard metrics.

## Post-launch validation plan

Once mainnet is live, validation becomes quantitative rather than indicative:

| Metric | Target Q1 post-launch | Source |
|---|---|---|
| Monthly active wallets | 500+ | On-chain |
| Matches per month | 10,000+ | On-chain (settled matches) |
| SC-share-record holders | 676/contract | On-chain (record registry) |
| Builder portal active publishers | 3–5 | On-chain (registered games) |
| Quarterly Incubation report cadence | Every 90 days | Public publication |

These targets are conservative for Q1; they are first-quarter operational benchmarks, not full-year goals. Real growth comes from compounding the audience that already exists at pre-launch + the post-launch acquisition channels described in [06 — Market, GTM, Competition](./06-market-gtm-competition.md).

---

**Read next:** [06 — Market, GTM, Competition](./06-market-gtm-competition.md) → bottom-up market logic and acquisition channels.
