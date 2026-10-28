# Scoring, Technical Validation and Model Limitations

This page defines how the public documentation should discuss AI-QSIS scores and validations without claiming more than has been demonstrated. It is intentionally explicit where implementation details still need verification.

## 1. Separate the kinds of outputs

AI-QSIS workbook fields fall into several distinct classes:

- **Observed or sourced data:** prices, volume, 52-week values and available financial metrics.
- **Derived indicators:** price changes, moving averages, relative volume, RSI/MACD-related values and price-position measures.
- **Component scores:** technical, growth, quality, valuation, volume, acceleration and profitability-trajectory scores.
- **Composite scores and ranks:** `OverallScore`, `FuturePotentialScore`, `SectorScore`, `V8_OpportunityScore` and page-specific ranks.
- **Categorical labels:** `MarketBias`, `MarketPhase`, `PriceSignal`, `GrowthStage`, `RiskLevel`, `DailyState`, `LiveBuyingSignal`, `V8_Opportunity` and `UniverseStatus`.
- **Narrative fields:** `Strengths`, `Concerns`, `Warnings`, `AI_Summary`, `LongTermView`, scenario cases and `FinalReco`.

These types should not be treated as interchangeable. A raw metric is not a score, a rank is not a probability, and a narrative label is not proof of predictive accuracy.

## 2. What should be documented for every score

Before publishing exact methodology claims, verify and document:

1. **Definition:** what the score is intended to measure.
2. **Inputs:** exact fields, source, frequency, lookback and data timestamp.
3. **Transformations:** normalisation, clipping, imputation, scaling and outlier handling.
4. **Weights:** contribution of each component to any composite score.
5. **Thresholds:** rules mapping numerical scores to categories or signals.
6. **Missing data:** whether the row is skipped, penalised, imputed or calculated from fewer fields.
7. **Directionality:** whether higher is always better, or whether the scale is context-dependent.
8. **Versioning:** changes to formulas and thresholds across project versions.
9. **Evaluation:** historical tests showing how the score relates to an independently defined outcome.

Do not infer weights or formulas from column names or from one displayed row.

## 3. Data-quality checks to report

The workbook and run logs should be reviewed for checks such as:

- Missing or invalid ticker symbols and duplicate rows.
- Missing, stale, non-positive or implausible price/volume observations.
- Insufficient history for 52-week measures, moving averages, RSI, MACD or return windows.
- Financial metrics that are unavailable, stale, non-comparable or reported in inconsistent units.
- Division-by-zero and negative-denominator cases, especially for ratios and valuation metrics.
- Null, infinite or out-of-range score values.
- Score labels that do not match the relevant threshold rules.
- Sorting and ranking consistency, including ties.
- Excel output creation, expected sheet names, column presence, row counts and date-stamped filenames.
- Clear logging of skipped stocks and reasons for exclusion.

This is a recommended checklist, not a claim that every check is already implemented. Mark each check as implemented, partially implemented, manual, or planned only after reviewing the source.

## 4. Directional volume caveat

Fields such as `BuyVolume_1D`, `SellVolume_1D`, `BuyVolumePct`, `SellVolumePct`, `BuySellRatio`, `VolumePressure`, `SellingPressure`, `BuyingPressureScore` and related sector aggregates require a clear data-method note.

If these fields are estimated from daily OHLCV candle direction or close location, they should be described as **estimated directional-volume indicators**. Daily OHLCV data does not identify the actual aggressor side of each trade. Avoid presenting such estimates as exchange-confirmed buyer/seller flow unless the data source and implementation support that claim.

## 5. Historical evaluation needed for predictive claims

To evaluate whether rankings or signals have predictive value, a separate testing process should specify:

- The outcome being predicted (for example, forward return over a clearly stated horizon).
- The universe and historical inclusion rules, including delisted or unavailable securities where relevant.
- Point-in-time data availability to avoid look-ahead and survivorship bias.
- A chronological train/validation/test split or walk-forward process.
- Transaction costs, slippage, liquidity constraints and realistic execution assumptions where applicable.
- Benchmarks and baseline strategies.
- Metrics appropriate to the objective, with uncertainty and sample size reported.
- Stability across periods, market regimes and sectors.
- Controls against tuning repeatedly to the same test period.

Do not describe a score as predictive, profitable, backtested or validated unless there is evidence and documented methodology supporting that statement.

## 6. Scenario fields

`BullCase`, `BaseCase` and `BearCase` should be explained as scenario-style outputs. The public README should clarify whether they are rule-generated text, model-generated narratives, or numerically modelled scenarios only after the implementation is checked. Do not call them price targets or probabilities unless that is actually how they are produced and calibrated.

## 7. Risk labels and recommendations

`RiskLevel` is a system-assigned category. Unless calibrated against realised outcomes, it should not be described as a probability of loss, a regulatory risk rating or a guarantee that a stock is safe. `FinalReco`, `Priority`, `LongTermView`, `DailyState` and similar labels should be explained through their actual thresholds/rules and positioned as research aids.

## 8. Release checklist for the public project

- [ ] Confirm every published sheet name and its actual selection/filter rules.
- [ ] Verify score definitions, scales, weights and thresholds against the source.
- [ ] Document source providers, refresh cadence and timestamps.
- [ ] Confirm financial-metric units and reporting periods.
- [ ] Validate missing-data and error handling.
- [ ] Distinguish estimated directional volume from confirmed trade-flow data.
- [ ] Label historical performance claims only when supported by reproducible tests.
- [ ] Keep private implementation, secrets, credentials and proprietary formulas out of the public repository where required.
- [ ] Ensure README examples match the same workbook/run version.
