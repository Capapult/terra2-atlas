# TERRA² · ATLAS

A live, single-file dashboard for the Terra2 (`phoenix-1`) ecosystem.

> Apple precision, Tesla innovation. The chain that refused to die, mapped in real time.

## What's in it

- **Heartbeat strip** — block height & EKG trace pulse on every new block (~6 s)
- **Vibe ring** — Apple-Watch-style activity ring synthesising TVL momentum, price momentum and active-protocol count
- **Constellation** — every alive Terra2 dApp as a glowing node, sized by TVL, coloured by category, faded if dormant. Click to open a side panel with live stats
- **TVL chart** — 30-day chain TVL with current marker
- **Liquid LUNA** — ampLUNA & boneLUNA spot prices, 24h change, exchange rate
- **Validator orbit** — top 10 validators in animated planetary motion around phoenix-1
- **Solid Protocol spotlight** — featured (CAPA, ampCAPA, Astral, Atrium, Peg Press, Crystals)
- **Frontier** — alive vs. departed venues, an honest map

## Data sources (all free, no auth)

| What | Endpoint |
|---|---|
| Block, validators, supply, pool, inflation | `terra-rest.publicnode.com` (Cosmos LCD, CORS-enabled) |
| Per-protocol Terra2 TVL | `api.llama.fi/protocols` (DefiLlama) |
| Chain TVL history | `api.llama.fi/v2/historicalChainTvl/Terra2` |
| Spot prices · primary | `api.coingecko.com/api/v3/simple/price` |
| Spot prices · fallback | `coins.llama.fi/prices/current/coingecko:…` |
| 24h change · fallback | `coins.llama.fi/percentage/coingecko:…` |

When CoinGecko rate-limits (429), the dashboard falls back to DefiLlama coins automatically and patches the last-known market cap from `localStorage` — so it never goes blank.

## Refresh cadence

- Chain LCD (block, validators, pool): every **6 s**
- Prices: every **30 s**
- DefiLlama TVL: every **60 s**
- Heartbeat trace: every **40 ms** (interpolated)
- Sticky timestamp on the pulsebar shows seconds since last successful refresh.

## Running locally

It's a single static `index.html`. Serve any way you want:

```bash
python3 -m http.server 5174 --directory .
```

Then open `http://localhost:5174`.

No build step. No npm. No keys.

## Deploy

Drop `index.html` on any static host (Cloudflare Pages, Vercel, GitHub Pages, S3+CloudFront). Suggested public URLs:

- `terra2.solidcapa.com`
- `atlas.solidcapa.com`
- `phoenix-1.solidcapa.com`

## Files

- `index.html` — the whole thing (HTML + CSS + JS, ~72 kB)
- `.claude/launch.json` — local preview config
- `README.md` — this file

Build: 1.0 · 2026-05-07
