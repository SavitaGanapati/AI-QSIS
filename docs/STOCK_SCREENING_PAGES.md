# Stock Screening Pages: All Stocks and Candidate Lists

This guide explains the broad stock table and the candidate lists that reuse its column schema.

## All Stocks: the detailed research record

The All Stocks page combines these families of fields:

1. **Identity and price range:** `Ticker`, `Stock`, `Sector`, `CP`, `52L`, `52H`, `PricePositionPct`, `PricePosition`, `DrawdownFrom52H`, `(%)FromLow`.
2. **Market context:** `MarketBias`, `BullishPoints`, `BearishPoints`, `MarketPhase`, `PriceSignal`.
3. **Momentum and relative strength:** `PriceChange1D`, `PriceChange5D`, `PriceChange20D`, `RSI`, `RS`, `SMA50`, `SMA200`, `MACD`, `Signal`.
4. **Volume behaviour:** `VolRatio`, `VolumeStrength`, `CurrentVolume`, `AvgVolume20`, `BuyVolume_1D`, `SellVolume_1D`, `BuyVolumePct`, `SellVolumePct`, `BuySellRatio`, `VolumePressure`, `SellingPressure`, `BuyVolumeScore`, `SellVolumeScore`, `VolumeScore`.
5. **Factor scores:** `CAGR`, `Score`, `TechnicalScore`, `GrowthScore`, `QualityScore`, `ValuationScore`, `OverallScore`.
6. **Fundamental metrics:** `RevGrowth`, `ROE`, `DebtEq`, `ProfitMargin`, `EPSGrowth`, `PE`.
7. **Long-term growth features:** `RevenueAccelerationScore`, `EarningsAccelerationScore`, `MarginExpansionScore`, `ProfitabilityTrajectoryScore`, `FuturePotentialScore`, `GrowthStage`.
8. **Risk and narrative:** `RiskLevel`, `LongTermView`, `BullCase`, `BaseCase`, `BearCase`, `Strengths`, `Concerns`, `Warnings`, `AI_Summary`, `FinalReco`.

Use this page to examine the evidence behind a candidate. Confirm the period, unit, source and formula for each metric before comparing values across stocks.

## Emerging Growth

This tab uses the broad stock schema. Its purpose is to display stocks selected as emerging-growth candidates. The actual qualification logic—thresholds, exclusions, missing-data handling and sorting—must be described from code, not inferred from the page name.

## Breakout_candidates

This tab also uses the broad stock schema and is intended for breakout-related review. The project documentation should state the exact breakout definition, price/volume conditions, lookback windows, and data timing used by the implementation. The word “candidate” is important: a potential breakout can fail.

## Reversal candidates

This tab uses the broad stock schema for reversal-related review. Document the specific rules that select candidates and what evidence would count as confirmation. A fall toward a low or a single changing indicator does not prove a reversal.

## EOD candidates

This tab uses the broad stock schema for end-of-day review. To substantiate the EOD label, document the data snapshot time, whether prices are final closing prices, and the selection rule. If the workbook is generated before the official close or from delayed data, state that limitation clearly.

## Premarket Strength

The supplied page has a focused schema: `Stock`, `Sector`, `CP`, `MarketBias`, `RS`, `SMA50`, `SMA200`, `CAGR`, `RevGrowth`, `EPSGrowth`, `ROE`, `DebtEq`, `ProfitMargin`, `PE`, `GrowthScore`, `QualityScore`, `ValuationScore`, `TechnicalScore`, `OverallScore`, the four growth-acceleration/profitability scores, `FuturePotentialScore`, `GrowthStage`, `RiskLevel`, `LongTermView`, `Strengths`, `Concerns`, `Warnings`, `AI_Summary`, and `FinalReco`.

The view combines market/technical and longer-term information. The page name alone does not establish that all fields are available before the market opens. Document the source timestamps and update schedule before claiming premarket freshness.

## Near-52-week-low pages

The `within 10 percent low`, `5% low`, and `2 percent low` pages use the broad stock schema and are intended to show different proximity-to-low filters. The exact calculation must be verified. Possible fields relevant to the interpretation include `52L`, `52H`, `PricePositionPct`, `PricePosition`, `DrawdownFrom52H`, and `(%)FromLow`, but do not assume which field drives the filter without reviewing the code.

Being close to a 52-week low describes price location; it does not establish undervaluation. It can also reflect deteriorating business performance or elevated risk. Review the fundamentals, warnings, and scenario fields.

## Repeated columns are intentional context, not proof of repeated calculations

Several tabs share the same column schema because they present different subsets of stocks for different research questions. However, identical headers do not prove identical filtering logic, refresh timing, or ranking criteria. Each tab's row-selection rules should be independently documented.
