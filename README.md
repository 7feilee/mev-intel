# MEV Intelligence — daily Ethereum bot report

[![brief](https://img.shields.io/badge/brief-2026--07--15-2ea44f)](briefs/2026-07-15.md)
[![bots](https://img.shields.io/badge/profitable%20bots-2,759-blue)](data/feed.json)
[![aggregate](https://img.shields.io/badge/weekly%20net-%2425.5M-orange)](data/feed.json)

**A daily, machine-generated intelligence report on Ethereum MEV bots** — who is actually
earning, which new bots are rising, the on-chain strategy mix, and a live mempool watch of
front-running / sandwich / backrun activity. Everything is computed from a **self-hosted
`reth` archive node** and an open MEV-classification pipeline — no third-party APIs.

> 2,759 bots cleared measurable profit this week ($25,479,171 aggregate, high-confidence, pre-bribe), out of 27,270 active. The board is top-heavy: 0x4cd4499d… leads at $2,187,101/wk (148 tx, mixed), with 15 bots above $100k/wk. No notable new entrants. Actionable: the concentration means a handful of operators define inclusion pricing; track their builder mix before competing on any pair they touch.

---

*Ethereum L1 · trailing 7 days · 27,270 active bots · 2,759 profitable · aggregate $25,479,171/wk (high-confidence, pre-bribe)*

## Executive summary
2,759 bots cleared measurable profit this week ($25,479,171 aggregate, high-confidence, pre-bribe), out of 27,270 active. The board is top-heavy: 0x4cd4499d… leads at $2,187,101/wk (148 tx, mixed), with 15 bots above $100k/wk. No notable new entrants. Actionable: the concentration means a handful of operators define inclusion pricing; track their builder mix before competing on any pair they touch.

## Top earners

| # | Bot | Net/wk | Tx/wk | Strategy |
|--|--|--|--|--|
| 1 | `0x4cd4499d6e6a…` | $2,187,101 | 148 | — |
| 2 | `0x00000000fd3a…` | $1,948,171 | 3,860 | — |
| 3 | `0x95480d3f2765…` | $1,677,008 | 856 | — |
| 4 | `0x924465cf8cfc…` | $1,142,648 | 866 | — |
| 5 | `0x95dd8db1c0c0…` | $883,576 | 1,174 | — |
| 6 | `0xd90acddac86e…` | $851,317 | 1,011 | — |
| 7 | `0xb1b2d032aa2f…` | $754,887 | 6,831 | — |
| 8 | `0xe1066ffcb695…` | $734,358 | 49 | — |
| 9 | `0x2f4e1a92dd8d…` | $652,452 | 927 | — |
| 10 | `0xa7842153fde3…` | $630,586 | 61 | — |
| 11 | `0x6bf97afe2d2c…` | $582,323 | 626 | — |
| 12 | `0xb9332b6301e5…` | $502,892 | 2,760 | — |
| 13 | `0xa60ded4c899e…` | $455,427 | 2,208 | — |
| 14 | `0x6e2c8549ecc8…` | $341,604 | 947 | — |
| 15 | `0x9d56e8efd23d…` | $335,342 | 876 | — |

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
