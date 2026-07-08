# MEV Intelligence — daily Ethereum bot report

[![brief](https://img.shields.io/badge/brief-2026--07--08-2ea44f)](briefs/2026-07-08.md)
[![bots](https://img.shields.io/badge/profitable%20bots-1,378-blue)](data/feed.json)
[![aggregate](https://img.shields.io/badge/weekly%20net-%2416.4M-orange)](data/feed.json)

**A daily, machine-generated intelligence report on Ethereum MEV bots** — who is actually
earning, which new bots are rising, the on-chain strategy mix, and a live mempool watch of
front-running / sandwich / backrun activity. Everything is computed from a **self-hosted
`reth` archive node** and an open MEV-classification pipeline — no third-party APIs.

> 1,378 bots cleared measurable profit this week ($16,363,783 aggregate, high-confidence, pre-bribe), out of 17,276 active. The board is top-heavy: 0xe91fb2ca… leads at $1,835,789/wk (383 tx, mixed), with 15 bots above $100k/wk. No notable new entrants. Actionable: the concentration means a handful of operators define inclusion pricing; track their builder mix before competing on any pair they touch.

---

*Ethereum L1 · trailing 7 days · 17,276 active bots · 1,378 profitable · aggregate $16,363,783/wk (high-confidence, pre-bribe)*

## Executive summary
1,378 bots cleared measurable profit this week ($16,363,783 aggregate, high-confidence, pre-bribe), out of 17,276 active. The board is top-heavy: 0xe91fb2ca… leads at $1,835,789/wk (383 tx, mixed), with 15 bots above $100k/wk. No notable new entrants. Actionable: the concentration means a handful of operators define inclusion pricing; track their builder mix before competing on any pair they touch.

## Top earners

| # | Bot | Net/wk | Tx/wk | Strategy |
|--|--|--|--|--|
| 1 | `0xe91fb2ca6287…` | $1,835,789 | 383 | — |
| 2 | `0xd90acddac86e…` | $1,251,025 | 1,196 | — |
| 3 | `0xe7aa802e19c9…` | $1,042,405 | 287 | — |
| 4 | `0xe49384e6aca6…` | $954,505 | 70 | — |
| 5 | `0x7f62d903e835…` | $884,206 | 112 | — |
| 6 | `0xb1b2d032aa2f…` | $679,439 | 8,143 | — |
| 7 | `0x3eb5ba7f6086…` | $572,494 | 856 | — |
| 8 | `0xb9332b6301e5…` | $401,513 | 2,522 | — |
| 9 | `0x95480d3f2765…` | $387,770 | 1,301 | — |
| 10 | `0x6bf97afe2d2c…` | $333,689 | 927 | — |
| 11 | `0xdf8198746568…` | $315,620 | 184 | — |
| 12 | `0xace00000a77b…` | $284,145 | 63 | — |
| 13 | `0xdca8dcb31aa2…` | $221,350 | 24 | — |
| 14 | `0xeeb65da7e686…` | $215,587 | 203 | — |
| 15 | `0xa7842153fde3…` | $214,377 | 76 | — |

## Live mempool watch

Over the last ~40h of pending-tx monitoring (12,102 blocks, 10,877 distinct bots):

| Signal | Count |
|--|--|
| backrun | 19,544 |
| generalized frontrun | 6,726 |
| displacement | 4,871 |
| sandwich | 2,065 |

**9,094 bot-vs-bot 'MEV war' events** — the dominant pattern is bots front-running and backrunning *each other*, not just users.

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
- [2026-07-08](briefs/2026-07-08.md)
- [2026-07-07](briefs/2026-07-07.md)
- [2026-07-06](briefs/2026-07-06.md)

---
*Auto-generated daily. Not financial advice. Built by [@7feilee](https://github.com/7feilee).*
