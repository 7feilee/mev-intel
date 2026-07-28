# MEV Intelligence — daily Ethereum bot report

[![brief](https://img.shields.io/badge/brief-2026--07--28-2ea44f)](briefs/2026-07-28.md)
[![bots](https://img.shields.io/badge/profitable%20bots-4,143-blue)](data/feed.json)
[![aggregate](https://img.shields.io/badge/weekly%20net-%2433.0M-orange)](data/feed.json)

**A daily, machine-generated intelligence report on Ethereum MEV bots** — who is actually
earning, which new bots are rising, the on-chain strategy mix, and a live mempool watch of
front-running / sandwich / backrun activity. Everything is computed from a **self-hosted
`reth` archive node** and an open MEV-classification pipeline — no third-party APIs.

> 4,143 bots cleared measurable profit this week ($32,964,849 aggregate, high-confidence, pre-bribe), out of 33,102 active. The board is top-heavy: 0x9d56e8ef… leads at $1,559,055/wk (971 tx, mixed), with 15 bots above $100k/wk. No notable new entrants. Actionable: the concentration means a handful of operators define inclusion pricing; track their builder mix before competing on any pair they touch.

---

*Ethereum L1 · trailing 7 days · 33,102 active bots · 4,143 profitable · aggregate $32,964,849/wk (high-confidence, pre-bribe)*

## Executive summary
4,143 bots cleared measurable profit this week ($32,964,849 aggregate, high-confidence, pre-bribe), out of 33,102 active. The board is top-heavy: 0x9d56e8ef… leads at $1,559,055/wk (971 tx, mixed), with 15 bots above $100k/wk. No notable new entrants. Actionable: the concentration means a handful of operators define inclusion pricing; track their builder mix before competing on any pair they touch.

## Top earners

| # | Bot | Net/wk | Tx/wk | Strategy |
|--|--|--|--|--|
| 1 | `0x9d56e8efd23d…` | $1,559,055 | 971 | — |
| 2 | `0xaa34d20be3f9…` | $1,497,799 | 161 | — |
| 3 | `0x3980daa7eaad…` | $1,439,108 | 969 | — |
| 4 | `0xd90acddac86e…` | $1,262,347 | 518 | — |
| 5 | `0x6bf97afe2d2c…` | $1,029,247 | 216 | — |
| 6 | `0xb1b2d032aa2f…` | $920,796 | 6,134 | — |
| 7 | `0x924465cf8cfc…` | $916,168 | 970 | — |
| 8 | `0xa6eabd41ff33…` | $886,889 | 60 | — |
| 9 | `0x95480d3f2765…` | $801,557 | 2,652 | — |
| 10 | `0x71f12a5b0e60…` | $726,573 | 134 | — |
| 11 | `0x9f09502a0b68…` | $645,207 | 88 | — |
| 12 | `0x898e5fd573a8…` | $643,034 | 65 | — |
| 13 | `0xa60ded4c899e…` | $578,920 | 1,610 | — |
| 14 | `0x3eb5ba7f6086…` | $575,389 | 979 | — |
| 15 | `0xbdfa4f4492dd…` | $495,483 | 57 | — |

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
- [2026-07-28](briefs/2026-07-28.md)
- [2026-07-27](briefs/2026-07-27.md)
- [2026-07-26](briefs/2026-07-26.md)
- [2026-07-25](briefs/2026-07-25.md)
- [2026-07-24](briefs/2026-07-24.md)
- [2026-07-23](briefs/2026-07-23.md)
- [2026-07-22](briefs/2026-07-22.md)
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
