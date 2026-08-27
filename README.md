<div align="center">

# 🔧 CF OSINT Toolkit

**Production patterns for building OSINT tools on Cloudflare's edge — D1 · KV · R2 · Cron · AT Protocol**

[![Cloudflare Workers](https://img.shields.io/badge/Cloudflare_Workers-F38020?style=for-the-badge&logo=cloudflare&logoColor=white)](https://workers.cloudflare.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)
[![VPDLNY](https://img.shields.io/badge/VPDLNY-Open_Source-8B0000?style=for-the-badge)](https://osintnet.uk)

</div>

---

## What Is This

A battle-tested collection of Cloudflare Workers patterns extracted from real OSINT tools in production. Built by [VPDLNY](https://osintnet.uk) running 145+ workers, each on its own dedicated custom domain.

Use these as starters, templates, or reference implementations for your own intelligence tools.

---

## Patterns Included

| Pattern | Description | Storage |
|---------|-------------|---------|
| `news-aggregator` | NewsAPI + KV caching with TTL | KV |
| `d1-heatmap-api` | REST API over D1 for map data | D1 |
| `bsky-poster` | AT Protocol post with image embed | KV |
| `campaign-drip` | Scheduled thread posting engine | D1 |
| `cron-digest` | Daily digest via Telegram/email | KV |
| `btc-gating` | Bitcoin payment verification gateway | KV |
| `leaflet-worker` | Full Leaflet.js app served from Worker | Static |
| `r2-cdn` | R2-backed image CDN with custom domain | R2 |

---

## Architecture Philosophy

```
Every OSINT tool follows this pattern:

1. CF Worker  →  handles all HTTP (no server, no cold start)
2. D1         →  primary structured data (SQLite at edge)
3. KV         →  cache, rate limits, short-lived flags
4. R2         →  images, PDFs, blobs
5. Cron       →  scheduled refreshes (max 5/account on free)
6. CF Access  →  Zero Trust auth for admin endpoints
```

---

## Quick Start

```bash
# Clone the toolkit
git clone https://github.com/indicaindependent/cf-osint-toolkit
cd cf-osint-toolkit

# Pick a pattern
cd patterns/news-aggregator

# Configure
cp wrangler.toml.example wrangler.toml

# Deploy
npm install -g wrangler
wrangler login
wrangler deploy
```

---

## Related Tools (Live in Production)

- 🌍 [WarHeatMap](https://warheatmap.app) — Global conflict map
- 🔭 [EdgeIntel](https://intel.osintnet.uk) — OSINT news aggregator

---

## License

[MIT](LICENSE) — Build freely. Credit appreciated.

---

<div align="center">
<sub>Extracted from 145+ production workers | <a href="https://osintnet.uk">Indica Independent</a></sub>
</div>


---

## ⚡ Support the Mission

This is free, ad-free, independent infrastructure — no VC, no gov funding, no strings. If it served you, a tip keeps it alive and funds the next tool.

[![Donate via SkyGive](https://img.shields.io/badge/💜_Donate_via_SkyGive-8A5CF6?style=for-the-badge&logoColor=white)](https://donate.skygive.app/)
[![Lightning](https://img.shields.io/badge/⚡_tips@skygive.app-F7931A?style=for-the-badge&logo=lightning&logoColor=white)](https://donate.skygive.app/)

<sub>🧡 Sovereign Lightning + on-chain via SkyGive. Your sats fund uptime, not ads.</sub>
