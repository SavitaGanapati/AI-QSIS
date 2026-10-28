# Data, Methodology, and Risk Notes

## Data quality
Document the market-data provider, timestamp, reporting period, units, adjustment policy, and handling of missing or stale data for each field. The public screenshots alone do not establish every data-quality rule.

## Directional volume
Buy/sell-volume percentages derived from OHLCV candles should be treated as estimates unless verified trade-level aggressor-side data is used. Candle direction or close location does not prove the initiator of every trade.

## Scores and labels
Scores are system-generated indicators. Do not call them probabilities, expected returns, or calibrated forecasts unless the methodology and validation support those interpretations. Record component definitions, score ranges, weights, thresholds, and treatment of missing inputs.

## Risk labels
A system-assigned risk category is not a guarantee against loss. Document the rule or model that assigns each label and evaluate whether the labels correspond to realised outcomes.

## Validation
Separate software/data validation from predictive validation. Software checks can test schemas, ranges, missing values, calculations, and file generation. Predictive claims require leakage-aware historical evaluation, preferably out-of-sample or walk-forward, and consideration of survivorship bias, corporate actions, liquidity, transaction costs, and realistic execution.

## Investment-use boundary
The project is a research and educational decision-support tool. It does not provide personalised investment advice or guarantee returns.
