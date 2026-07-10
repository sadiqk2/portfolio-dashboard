# Live Markets Dashboard

A **real-time, multi-asset** dashboard powered entirely by **public, keyless APIs** —
a crypto portfolio, live FX rates, and precious-metals spot. Built client-side with
**hand-drawn SVG charts** (no chart library, no backend, no API keys).

**Live:** https://sadiqk2.github.io/portfolio-dashboard

![dashboard](docs/preview.png)

## Two views

**Crypto Portfolio** — live prices, 24h change, market cap and 7-day sparklines from
[CoinGecko](https://www.coingecko.com/en/api):
- KPI tiles (value + live sparkline, 24h P&L, best mover, assets held)
- 7-day portfolio-value curve (summed from each asset's sparkline × your quantity), 24h-change diverging bars, allocation donut, sortable holdings table
- **Editable holdings** (persisted to `localStorage`), **currency switch** (EUR / USD / GBP / JPY), and **add/remove assets** (track up to 8), 60s auto-refresh

**FX & Metals** — live foreign-exchange and metals:
- ECB reference rates via [Frankfurter](https://frankfurter.dev) with a selectable base currency and a **30-day trend chart** for any pair (real history endpoint)
- **Gold & silver spot** via [gold-api](https://gold-api.com), converted into your base currency using the live FX rates

## Why these sources

GitHub Pages is static, so the browser calls each API directly — which means every
source must be **keyless and CORS-enabled** (`access-control-allow-origin: *`).
CoinGecko, Frankfurter/ECB and gold-api all qualify. (There's no keyless *commodity*
API beyond gold/silver, and metals have no public history, so metals are spot-only.)
On a rate-limit the UI keeps the last good data and shows a clear status.

## Design notes

Chart colors follow a **CVD-safe categorical palette** validated with a colorblindness
+ contrast checker (fixed hue order; donut segments carry direct labels and 2px gaps).
Diverging P&L uses a blue↔red pair with a neutral zero axis; green/red is reserved for
gain/loss text. Light and dark themes; `prefers-reduced-motion` respected.

## Run locally

```bash
python3 -m http.server 8000   # open http://localhost:8000
```

Single `index.html`, no build step.
