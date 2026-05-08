# split-lp-fixer

Maps a 2026 split 1 NA League rank to its 2025 NA percentile equivalent.

Live: https://machineloling-hub.github.io/split-lp-fixer/

## How it works

Two-step quantile inversion:

1. Compute the percentile of your 2026 rank within the full NA ladder, using a 2026 split 1 NA snapshot (1.085M players, Master+ at 100-LP precision).
2. Find the 2025 rank covering the same percentile, using Riot's published 2025 distribution (~1M total, 0.69% Master+, 2.56% Diamond, etc.).

LP within a 2025 division is interpolated linearly (0–99). Real distributions skew low, so the true 2025 spot is often a half-division more inflated than the linear estimate.

Master+ output LP is reported in 2026's LP scale — there is no LP-level data for 2025, so the model assumes the conditional LP distribution within Master+ is preserved year-over-year.

## Data sources

- 2026 split 1 NA snapshot (`MP_2026`, `DIVS_2026` in `index.html`).
- 2025 NA tier %, sourced from Riot's published distribution.

## Deploy

Static. `index.html` is everything. GitHub Pages serves it from `main` / root.
