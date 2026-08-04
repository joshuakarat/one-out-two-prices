# One Outcome, Two Prices?

[**Read the paper**](paper/output/Joshua_Karat_One_Outcome_Two_Prices_v3.2.0.pdf) · [**View the project page**](index.html) · [**Inspect the result manifest**](results/results_manifest.json)

Reproducible research package for:

> **One Outcome, Two Prices? Rule-Verified No-Arbitrage and Price Discovery in Event-Contract Probability Surfaces**

The project studies two Kalshi contract families written on the same end-of-day S&P 500 and Nasdaq-100 index values: mutually exclusive range claims and nested threshold claims. For adjacent boundaries, their terminal payoffs satisfy the model-free identity

\[
\mathbf{1}\{K_i \le S_T < K_{i+1}\}
=
\mathbf{1}\{S_T \ge K_i\}
-
\mathbf{1}\{S_T \ge K_{i+1}\}.
\]

Rule-verified redundancy permits a within-exchange audit of price coherence, executable quote bounds, global probability surfaces, error correction, and forecasting without estimating fundamental value.

## Headline findings

- 2,106 exact state matches across 86 events on 43 trading dates.
- 64,819 same-minute, all-leg quote rows, but a median of only four quoted minutes per event-state; the top 10% of pairs generate 48.4% of rows.
- Direct-versus-synthetic midpoint correlation of 0.9913 and a one-cent median absolute gap.
- 862 gross quoted-lock candidates (1.330%). In the pre-close sample, 849 minutes collapse to 607 episodes; direct-member all-taker fees leave 280 episodes and non-direct whole-cent precision leaves five across three events.
- Candidate composition is price-dependent: 74.5% of direct-member all-taker positives have reference midpoints at or below five cents, while no non-direct positive does.
- The conventional error-correction OLS estimate is shared-lag-noise sensitive. Full-sample OLS implies 69.1% one-minute repair and OLS on the exact 25,529-row IV sample implies 59.6%, versus 19.6% under IV; sample continuity matters, but the fixed-sample estimator change accounts for about four fifths of the attenuation at the point estimates.
- Overidentified lag-two/lag-three IV has a joint first-stage F of 276.8, passes equation-specific Hansen diagnostics, and estimates a 3.18-minute gap half-life with a [2.35,4.36] date-cluster bootstrap interval; the direct response is reliable and the synthetic response imprecise. Component-share uncertainty uses whole-date bootstrap and Fieller inference rather than a delta-method interval.
- A two-state placebo changes correlation from 0.985 on the common overlap to -0.058 and reduces total OLS gap adjustment from 69.1% to 1.0% per minute.
- Across 68 complete 30-state snapshots, there are zero executable direct-package and threshold-monotonicity violations.
- A joint linear programme finds 34 of 53 fixed-horizon surfaces feasible and 19 requiring at most one cent of quote relaxation; 11 failures are invisible to pairwise lock screens.
- No robust proper-score gain from forecast reconciliation in either the balanced individual-claim or complete-surface sample.

These are market-quality diagnostics. The data do not establish realised arbitrage profits or a deployable strategy.

## Project outputs

- `paper/output/` — publication PDF and editable DOCX;
- `paper/paper.md` and `paper/references.bib` — source and bibliography;
- `results/results_manifest.json` — machine-readable headline results;
- `results/tables/` — aggregate and derived analysis tables;
- `results/figures/` — ten publication figures;
- `src/`, `scripts/`, and `tests/` — collection, matching, analysis, publication, and verification code.

## Reproduce privately

The scripts require Python 3.11+ and the packages in `pyproject.toml`. Pandoc and XeLaTeX are additionally required to rebuild the PDF. The collector uses Kalshi's documented market-data API. Confirm that the intended use is authorised before collecting or publishing data.

```bash
python scripts/collect.py
python scripts/analyze.py
python scripts/build_paper.py
python -m unittest discover -s tests -v
```

The analysis fixes all random seeds and writes reported aggregates, figures, and a results manifest under `results/`. Wild-cluster tests use 4,999 draws; the IV noise null uses 999 replications; IV date-cluster and event-level forecast bootstraps use 10,000 resamples; and surface placebos use 1,000 permutations per event.

## Data and interpretation guardrails

Raw Kalshi data, row-level derived observations, and credentials are excluded from the distributable archive. Reproduction requires retrieving data directly under Kalshi's then-current agreement.

Historical one-minute candles contain closing top-of-book prices, not nanosecond-synchronised messages or historical depth. Positive bid/ask inequalities are therefore called **quoted lock candidates**, not realised or capacity-adjusted arbitrage profits. Maker-leg sensitivities do not assume resting orders fill atomically.

## Verification

The release passes 12 unit tests covering payoff identities, quote algebra, three fee regimes, lock detection, simplex projection, forecast fusion, and whole-surface feasibility. The PDF and DOCX are rendered and visually inspected page by page before delivery.
