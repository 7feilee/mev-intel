# MEV Intelligence — daily Ethereum bot report

[![brief](https://img.shields.io/badge/brief-2026--07--21-2ea44f)](briefs/2026-07-21.md)
[![bots](https://img.shields.io/badge/profitable%20bots-3,507-blue)](data/feed.json)
[![aggregate](https://img.shields.io/badge/weekly%20net-%2429.1M-orange)](data/feed.json)

**A daily, machine-generated intelligence report on Ethereum MEV bots** — who is actually
earning, which new bots are rising, the on-chain strategy mix, and a live mempool watch of
front-running / sandwich / backrun activity. Everything is computed from a **self-hosted
`reth` archive node** and an open MEV-classification pipeline — no third-party APIs.

> 3,507 bots cleared measurable profit this week ($29,054,449 aggregate, high-confidence, pre-bribe), out of 28,000 active. The board is top-heavy: 0xaa34d20b… leads at $1,488,516/wk (164 tx, mixed), with 15 bots above $100k/wk. No notable new entrants. Actionable: the concentration means a handful of operators define inclusion pricing; track their builder mix before competing on any pair they touch.

---

*Ethereum L1 · trailing 7 days · 28,000 active bots · 3,507 profitable · aggregate $29,054,449/wk (high-confidence, pre-bribe)*

## Executive summary
3,507 bots cleared measurable profit this week ($29,054,449 aggregate, high-confidence, pre-bribe), out of 28,000 active. The board is top-heavy: 0xaa34d20b… leads at $1,488,516/wk (164 tx, mixed), with 15 bots above $100k/wk. No notable new entrants. Actionable: the concentration means a handful of operators define inclusion pricing; track their builder mix before competing on any pair they touch.

## Top earners

| # | Bot | Net/wk | Tx/wk | Strategy |
|--|--|--|--|--|
| 1 | `0xaa34d20be3f9…` | $1,488,516 | 164 | — |
| 2 | `0x924465cf8cfc…` | $1,258,819 | 774 | — |
| 3 | `0xf204f3acb05c…` | $1,230,273 | 1,029 | — |
| 4 | `0xfdff0b569f14…` | $1,024,836 | 2,658 | — |
| 5 | `0x8661f478c6cc…` | $917,575 | 63 | — |
| 6 | `0xa7842153fde3…` | $730,529 | 170 | — |
| 7 | `0xd90acddac86e…` | $577,841 | 492 | — |
| 8 | `0x6bf97afe2d2c…` | $514,675 | 443 | — |
| 9 | `0xa60ded4c899e…` | $465,991 | 1,641 | — |
| 10 | `0x3eb5ba7f6086…` | $397,438 | 770 | — |
| 11 | `0xb1b2d032aa2f…` | $390,684 | 3,780 | — |
| 12 | `0xdbaa674ea606…` | $376,008 | 129 | — |
| 13 | `0xb9332b6301e5…` | $370,087 | 1,968 | — |
| 14 | `0x3980daa7eaad…` | $357,395 | 1,186 | — |
| 15 | `0x95d30549f608…` | $345,724 | 72 | — |

## Live mempool watch

Over the last ~40h of pending-tx monitoring (11,934 blocks, 19,353 distinct bots):

| Signal | Count |
|--|--|
| backrun | 24,080 |
| generalized frontrun | 12,328 |
| displacement | 12,463 |
| sandwich | 2,900 |

**18,863 bot-vs-bot 'MEV war' events** — the dominant pattern is bots front-running and backrunning *each other*, not just users.

---
*Generated automatically from a self-hosted Ethereum node + MEV pipeline. Not financial advice. Methodology below.*

---

## What this is
Each day this repo publishes:
- **Leaderboard** — the top MEV bots by measured 7-day net profit (quote-token deltas, high-confidence only, pre-builder-bribe).
- **New / rising entrants** — bots that just cracked the top ranks (the alpha).
- **Strategy mix** — atomic-arb vs backrun vs sandwich vs CEX-DEX, etc.
- **Live mempool watch** — front-run, displacement, sandwich, and backrun events seen in the public mempool, including bot-vs-bot "MEV wars".

Machine-readable feed: [`data/feed.json`](data/feed.json) (updated daily).

## Methodology (short)
Mined blocks are scanned via `eth_getBlockReceipts`; MEV txs are detected by log signature
(≥2 DEX swaps over ≥2 pools = arb, `LiquidationCall` = liquidation, Mint+Burn = JIT,
same-sender bracket = sandwich). Per-bot profit is the net quote-token (WETH/USDC/USDT/DAI)
delta. Bots settling in native ETH read ~$0 and are flagged, not trusted; flash-inflated
outliers are excluded. Numbers are **pre-builder-bribe** (coinbase transfers aren't visible
without traces), so treat them as upper bounds. The mempool watch polls `txpool_content` and
correlates pending txs with each new block.

## Archive
- [2026-07-21](briefs/2026-07-21.md)
- [2026-07-20](briefs/2026-07-20.md)
- [2026-07-19](briefs/2026-07-19.md)
- [2026-07-18](briefs/2026-07-18.md)
- [2026-07-17](briefs/2026-07-17.md)
- [2026-07-16](briefs/2026-07-16.md)
- [2026-07-15](briefs/2026-07-15.md)
- [2026-07-14](briefs/2026-07-14.md)
- [2026-07-13](briefs/2026-07-13.md)
- [2026-07-12](briefs/2026-07-12.md)
- [2026-07-11](briefs/2026-07-11.md)
- [2026-07-10](briefs/2026-07-10.md)
- [2026-07-09](briefs/2026-07-09.md)
- [2026-07-08](briefs/2026-07-08.md)
- [2026-07-07](briefs/2026-07-07.md)
- [2026-07-06](briefs/2026-07-06.md)

---
*Auto-generated daily. Not financial advice. Built by [@7feilee](https://github.com/7feilee).*
