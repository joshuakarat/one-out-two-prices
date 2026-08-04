# One Outcome, Two Prices?

**Rule-Verified No-Arbitrage and Price Discovery in Event-Contract Probability Surfaces**

This project tests whether two event-contract structures with identical settlement payoffs are priced consistently. Direct range contracts are matched to portfolios of adjacent threshold contracts on the same S&P 500 and Nasdaq-100 settlement values, creating a model-free, within-exchange test of price coherence and price discovery.

## Key findings

- Matched 2,106 payoff-equivalent states across 86 events and analysed 64,819 synchronous quote-minutes.
- Direct and synthetic prices have a 0.9913 correlation and a one-cent median absolute gap.
- Overidentified IV, designed to correct shared-lag quote-noise bias, estimates a 3.18-minute gap half-life with a 95% bootstrap interval of 2.35–4.36 minutes.
- Apparent arbitrage is not scalable: although the full panel contains 862 gross candidate state-minutes, the pre-close non-direct fee-positive screen yields only five episodes, worth approximately $0.10 in aggregate at one-lot size.

The central conclusion is negative but economically important: redundant contracts provide useful market-quality and price-discovery signals, but the data do not support a deployable arbitrage strategy.
