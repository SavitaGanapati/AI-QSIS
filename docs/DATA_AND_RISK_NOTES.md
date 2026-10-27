# Data, Methodology, and Risk Notes

## Data quality

- Confirm the timestamp and freshness of market data before interpreting a daily result.
- Handle missing, stale, duplicated, or inconsistent records explicitly.
- Verify symbol mappings and corporate-action adjustments.
- Review provider terms, usage limits, and redistribution restrictions.

## Directional-volume estimates

The supplied notebook states that its data source's OHLCV fields do not provide true buyer-initiated versus seller-initiated volume. Its directional-volume indicators are estimates based on candle direction and closing-price location. They should not be described as exchange-confirmed order-flow data.

## Scores and labels

Scores and labels are screening aids. They depend on the selected inputs, transformations, thresholds, and data availability. They should not be interpreted as calibrated probabilities or guaranteed forecasts unless separately tested and demonstrated.

## Validation checklist

- [ ] Check data coverage and missing values.
- [ ] Verify calculations against independently computed examples.
- [ ] Test edge cases such as zero volume, missing fundamentals, and short histories.
- [ ] Check for look-ahead bias and leakage from future information.
- [ ] Evaluate out-of-sample and walk-forward performance.
- [ ] Include realistic fees, slippage, liquidity, and execution constraints in any backtest.
- [ ] Compare with simple baselines.
- [ ] Document known limitations and version changes.

## Use disclaimer

AI-QSIS is for research and educational purposes only and does not provide personalized financial advice. No score, ranking, or classification guarantees investment performance.
