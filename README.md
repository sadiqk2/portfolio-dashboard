# Commodity Portfolio Dashboard

An interactive **position, P&L, exposure and allocation** dashboard for a book of
commodity trades — built entirely client-side with **hand-drawn SVG charts** (no
chart library, no backend).

**Live:** https://sadiqk2.github.io/portfolio-dashboard

![dashboard](docs/preview.png)

## Highlights

- **KPI tiles** — market value (with trend sparkline), unrealized P&L, open positions, net exposure.
- **Portfolio value** — 30-day area chart with a hover crosshair + tooltip and an emphasized endpoint.
- **Unrealized P&L by product** — diverging bars (gain right / loss left).
- **Allocation** — donut with direct labels, legend, and per-segment hover.
- **Positions table** — sortable columns, colored P&L, status pills, and **CSV export**.
- **Filters** — product, side, status, counterparty search — every view recomputes live.
- Light **and** dark themes; responsive; keyboard-focusable.

## Design notes

The chart colors follow a **CVD-safe categorical palette** validated against a
colorblindness + contrast checker (fixed hue order, ≥12 ΔE target; donut segments
carry direct labels and 2px gaps as the secondary encoding). Diverging P&L uses a
blue↔red pair with a neutral zero axis; status (good/critical) is a reserved palette
never reused for series color.

All data is **illustrative and generated deterministically in the browser** (seeded
PRNG) — these are not real trading positions.

## Run locally

```bash
python3 -m http.server 8000   # open http://localhost:8000
```

Single `index.html`, no build step.
