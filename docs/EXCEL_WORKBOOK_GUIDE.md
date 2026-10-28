# AI-QSIS Excel Workbook Guide

This guide explains the purpose of the workbook's major pages, how their columns should be interpreted, and how the views fit together. It is based on the output column lists supplied for AI-QSIS V8. Exact formulas, score weights, thresholds, filters, and sorting logic must be confirmed against the implementation; column names alone do not prove how a metric is calculated.

## How to use the workbook

1. Start with **VB Sector Rotation** and **VB Booming** to understand the system's sector-level view.
2. Use **VB Best Sector Stocks** to inspect individual opportunities in the selected sectors.
3. Use **All Stocks** for a broad, multi-factor view of the universe and to inspect supporting evidence, warnings, and scenario fields.
4. Review **LongTerm Ranking**, **Premarket Strength**, and **Emerging Growth** for different research questions rather than treating them as interchangeable rankings.
5. Use **Breakout_candidates**, **reversal candidates**, and **eod candidates** as separate candidate lists. Their names indicate intended use, but the exact selection rules must be verified in source.
6. Use the **within 10 percent low**, **5% low**, and **2 percent low** pages to examine stocks near their 52-week low according to the project's actual filter logic.
7. Read `RiskLevel`, `Warnings`, `Concerns`, scenario cases and `FinalReco` alongside scores. Do not make decisions from one score alone.

## Page-by-page guide

### 1. LongTerm Ranking

**Purpose:** provide a compact, prioritised long-term research list.

| Column | Interpretation |
|---|---|
| `Rank` | Position in this page's ranking. |
| `Stock`, `Sector` | Stock name and sector. |
| `Priority` | System-assigned priority label; exact rules need source verification. |
| `CP` | Current price as represented by the output. |
| `FuturePotentialScore` | System-generated long-term potential score. Its range, formula and weights should be documented from code. |
| `GrowthStage` | Growth-stage classification assigned by the system. |
| `RevGrowth` | Revenue-growth metric; period and units must be confirmed from the implementation/data source. |
| `RevenueAccelerationScore`, `EarningsAccelerationScore` | Scores associated with revenue and earnings acceleration. |
| `MarginExpansionScore` | Score associated with margin expansion. |
| `ProfitabilityTrajectoryScore` | Score representing a profitability trajectory. |
| `TechnicalScore`, `ValuationScore` | Technical and valuation components. |
| `RiskLevel` | System-assigned risk category, not a guarantee of safety. |
| `LongTermView` | Narrative long-term assessment. |
| `BullCase`, `BaseCase`, `BearCase` | Scenario-style narratives or assumptions; these are not guaranteed price targets unless the code explicitly defines them that way. |
| `FinalReco` | Final system-generated recommendation label. It is decision support, not personalised advice. |

**Interpretation note:** this page is the most compact long-term view. Use **All Stocks** when more context—such as technical indicators, financial metrics, warnings and AI summary—is needed.

### 2. All Stocks

**Purpose:** provide the broadest row-level research view, combining price context, market behaviour, technical indicators, fundamental metrics, scores, risk labels and explanatory text.

| Column group | Columns | How to read them |
|---|---|---|
| Identity and price | `Ticker`, `Stock`, `Sector`, `CP` | Identify the instrument, its sector and current price. |
| 52-week context | `52L`, `52H`, `PricePositionPct`, `PricePosition`, `DrawdownFrom52H`, `(% )FromLow` (actual header supplied as `(% )FromLow` without the space: `(%)FromLow`) | Compare the price with its 52-week range and assess distance from a high or low. Confirm the exact denominator and formula in code. |
| Market direction and points | `MarketBias`, `BullishPoints`, `BearishPoints` | Summarise the system's market-bias label and bullish/bearish point counts. Exact rules require source verification. |
| Price momentum | `PriceChange1D`, `PriceChange5D`, `PriceChange20D`, `RSI`, `RS` | Review recent price changes, RSI, and relative-strength measure. Confirm period, benchmark and scale for `RS`. |
| Moving averages | `SMA50`, `SMA200` | Price moving-average references over 50 and 200 periods; confirm frequency and handling of missing history. |
| Volume activity | `VolRatio`, `VolumeStrength`, `CurrentVolume`, `AvgVolume20`, `BuyVolume_1D`, `SellVolume_1D`, `BuyVolumePct`, `SellVolumePct`, `BuySellRatio`, `VolumePressure`, `SellingPressure`, `BuyVolumeScore`, `SellVolumeScore`, `VolumeScore` | Review current/average volume and the system's volume-related measures. Directional buy/sell fields may be estimates derived from OHLCV data, not confirmed buyer-initiated/seller-initiated exchange trades. |
| Market and technical signals | `MarketPhase`, `PriceSignal`, `MACD`, `Signal`, `TechnicalScore` | Inspect market-phase and price-signal labels, MACD-related fields and the technical score. Confirm indicator implementation and signal thresholds in source. |
| Growth and factor scores | `CAGR`, `Score`, `GrowthScore`, `QualityScore`, `ValuationScore`, `OverallScore` | Compare growth, quality, valuation and overall factor scores. The name `Score` is ambiguous without code-level definition; document its exact meaning before making claims. |
| Financial metrics | `RevGrowth`, `ROE`, `DebtEq`, `ProfitMargin`, `EPSGrowth`, `PE` | Review available revenue growth, return on equity, debt-to-equity, profit margin, EPS growth and price/earnings fields. Confirm periods, units, provider, and treatment of negative or missing values. |
| Long-term growth features | `RevenueAccelerationScore`, `EarningsAccelerationScore`, `MarginExpansionScore`, `ProfitabilityTrajectoryScore`, `FuturePotentialScore`, `GrowthStage` | Review the system's growth-related scores and classification. Scores are model outputs, not direct financial ratios unless specifically defined that way. |
| Risk and scenarios | `RiskLevel`, `LongTermView`, `BullCase`, `BaseCase`, `BearCase` | Consider risk category and the three scenario narratives together. Scenarios should be understood as conditional analysis, not certainty. |
| Explanation and decision support | `Strengths`, `Concerns`, `Warnings`, `AI_Summary`, `FinalReco` | Read the rationale and warnings before relying on a rank or recommendation label. Determine from implementation whether `AI_Summary` is rule-generated, model-generated, or produced by another process. |

**Interpretation note:** this page is a wide research table. It is best used to investigate *why* a stock received a particular score or label, not just to sort by `OverallScore` or `FuturePotentialScore`.

### 3. Premarket Strength

**Purpose:** present a focused view combining market bias, relative strength, moving averages, growth, quality, valuation, technical and overall scores.

| Column group | Columns | How to read them |
|---|---|---|
| Identity and market context | `Stock`, `Sector`, `CP`, `MarketBias`, `RS`, `SMA50`, `SMA200` | Identify the stock and inspect market-bias and relative-strength context. |
| Growth and fundamentals | `CAGR`, `RevGrowth`, `EPSGrowth`, `ROE`, `DebtEq`, `ProfitMargin`, `PE` | Review reported growth and fundamental fields; verify units and periods. |
| Factor scores | `GrowthScore`, `QualityScore`, `ValuationScore`, `TechnicalScore`, `OverallScore` | Compare the separate dimensions and overall score. Exact formula and weighting need source verification. |
| Long-term assessment | `RevenueAccelerationScore`, `EarningsAccelerationScore`, `MarginExpansionScore`, `ProfitabilityTrajectoryScore`, `FuturePotentialScore`, `GrowthStage` | Examine the long-term growth features even though the page is named for premarket strength. |
| Risk and explanation | `RiskLevel`, `LongTermView`, `Strengths`, `Concerns`, `Warnings`, `AI_Summary`, `FinalReco` | Read the system's risk category, explanatory text and final label. |

**Interpretation note:** the page name suggests a premarket use case, but the columns alone do not establish whether all source data is genuinely available before market open. Verify data timestamps and refresh schedule before describing it as a real-time premarket signal.

### 4. Emerging Growth

**Purpose:** surface stocks classified by the system as emerging-growth candidates.

The supplied column list is the same broad schema as **All Stocks**, including 52-week position, momentum, moving averages, volume indicators, technical signals, fundamental metrics, factor scores, growth-acceleration scores, risk labels, scenario fields and explanatory text.

**How to read it:** treat this as a filtered candidate view rather than a separate set of metrics. To explain why a stock qualifies, document the actual filter/threshold logic from code. Do not infer that every row is growing or that the label predicts future returns.

### 5. Breakout_candidates

**Purpose:** present a candidate list intended for breakout-related review.

The supplied schema matches **All Stocks**. This lets the reviewer inspect the same price, volume, technical, fundamental, risk and scenario context for each candidate.

**Validation needed:** document what constitutes a breakout in the implementation—for example, the actual price/volume conditions and lookback windows—rather than assuming a common definition. Confirm whether candidates are based on closing prices, intraday prices or another data snapshot.

### 6. Reversal candidates

**Purpose:** present a candidate list intended for reversal-related review.

The supplied schema matches **All Stocks**. Use the broader context to assess momentum, price position, volume indicators, technical measures, fundamentals and warnings.

**Validation needed:** document the actual reversal criteria and distinguish a possible reversal setup from a confirmed trend change. A stock near a low or showing a changing indicator is not automatically a successful reversal candidate.

### 7. EOD candidates

**Purpose:** present candidates for end-of-day review.

The supplied schema matches **All Stocks**. Its usefulness depends on the timing of the data snapshot and the rule used to select the candidates.

**Validation needed:** specify when the data is collected, whether prices are final/closing values, and what rule creates the EOD list. Do not call this an end-of-day signal unless the schedule and data semantics support that description.

### 8. VB Sector Rotation

**Purpose:** rank sectors using multiple time horizons and buying/volume/price confirmation indicators.

| Column | Interpretation |
|---|---|
| `SectorRank` | Sector's position in this view. |
| `Sector` | Sector name. |
| `SectorScore` | Composite sector score; component weights need source verification. |
| `DailyState` | System-assigned sector state. Document the exact categories and thresholds from code. |
| `Stocks` | Number of stocks included in the sector calculation/output. |
| `Avg1DReturn`, `Avg5DReturn`, `Avg20DReturn` | Average return measures across one-, five- and twenty-period horizons; verify whether these are trading days and how missing data is handled. |
| `BuyingPressureScore`, `VolumeSurgeScore` | Sector-level scores associated with buying-related activity and relative volume. |
| `BuyingBreadthPct` | Percentage measure based on the system's buying-related criteria. |
| `PriceConfirmationScore`, `TechnicalConfirmationScore` | Price and technical confirmation measures. Exact definitions require source verification. |
| `AvgBuyVolumePct`, `AvgSellVolumePct`, `AvgBuySellRatio`, `AvgVolumeRatio` | Sector-level aggregates of volume-related measures. Interpret directional buy/sell measures as estimates if they are derived from OHLCV candles. |

**Business use:** compare sector strength and consistency across multiple horizons before drilling into individual stocks. A high rank is relative to the universe and rules used for that run.

### 9. VB Booming

**Purpose:** provide a focused sector list associated with the system's booming/leading states.

The supplied columns match **VB Sector Rotation**. The principal difference appears to be the view/filter rather than the column schema; the exact filter should be confirmed in the implementation.

**Business use:** identify which sectors to inspect first, then use **VB Best Sector Stocks** to explore individual candidates.

### 10. VB Best Sector Stocks

**Purpose:** combine the broad stock research schema with sector-level and V8 opportunity indicators.

This page contains the full **All Stocks** set of columns plus:

| Additional column | Interpretation |
|---|---|
| `OpportunityRank` | Rank within this opportunity view. |
| `SectorScore` | Sector-level score associated with the stock's sector. |
| `NetBuyingPressurePct` | Net buying-related percentage measure; exact formula must be verified. |
| `LiveBuyingScore`, `LiveBuyingSignal` | V8 buying-related score and descriptive signal. Verify refresh timing and calculation before calling it live. |
| `V8_OpportunityScore`, `V8_Opportunity` | V8 opportunity score and label; exact components/thresholds require source verification. |
| `UniverseStatus` | Status assigned to the stock's universe membership or eligibility; document actual categories from code. |

**Business use:** connect the sector context to a stock-level view. A high `V8_OpportunityScore` is a screening result, not a trade execution command.

### 11. Within 10% Low, 5% Low and 2% Low

**Purpose:** provide progressively narrower lists of stocks near their 52-week lows, according to the project filters.

The supplied schema matches **All Stocks**. Relevant fields include `52L`, `52H`, `PricePositionPct`, `PricePosition`, `DrawdownFrom52H`, and `(%)FromLow`, alongside technical, volume, fundamental, risk and scenario fields.

**Validation needed:** verify whether each page filters by percentage distance above the 52-week low, `PricePositionPct`, another formula, or a combination. The names alone do not establish the exact calculation. Also check whether `52L`/`52H` are adjusted or unadjusted prices and how corporate actions or missing history are handled.

**Interpretation note:** being near a 52-week low is a price-location description, not proof of undervaluation or a likely rebound. Review the `Concerns`, `Warnings`, `RiskLevel` and financial metrics carefully.

## Cross-page field glossary

| Field | General meaning | Important caveat |
|---|---|---|
| `CP` | Current price in the output | Confirm currency, timestamp, exchange and adjustment basis. |
| `52L`, `52H` | 52-week low and high | Confirm lookback, adjusted/unadjusted data and missing-data rules. |
| `PricePositionPct` | Percentage-like position within the price range | Exact formula and scale must be verified. |
| `DrawdownFrom52H` | Distance/drawdown from the 52-week high | Confirm sign convention and percentage units. |
| `RSI` | Relative Strength Index field | Confirm lookback and implementation. |
| `RS` | Relative strength field | Do not assume benchmark, lookback or scale without code/data documentation. |
| `SMA50`, `SMA200` | Simple moving average fields | Confirm price frequency and number of observations. |
| `VolRatio` | Relative-volume ratio field | Confirm numerator, denominator and lookback. |
| `MACD`, `Signal` | MACD-related fields | Confirm whether `Signal` is the MACD signal line or a separate categorical field in each page. |
| `CAGR` | Compound annual growth rate field | Confirm underlying metric, period and annualisation. |
| `ROE`, `DebtEq`, `ProfitMargin`, `PE` | Fundamental/valuation fields | Confirm provider, fiscal period, units, outlier handling and negative-value treatment. |
| `OverallScore`, `Score` | General score fields | Ambiguous names require an explicit definition from the implementation. |
| `RiskLevel` | Assigned risk category | Not a calibrated probability of loss unless separately established. |
| `FinalReco` | Final recommendation label | Explain its rules and retain human review. |

## What a reader should not assume

- Similar column schemas do not prove that tabs use identical selection filters.
- A score's name does not establish its formula, scale, calibration or predictive validity.
- `Live` in a column name does not prove a live market feed or real-time refresh.
- A `BullCase`, `BaseCase` or `BearCase` label does not prove a statistically calibrated forecast.
- Directional volume estimates based on OHLCV candles are not the same as exchange-confirmed aggressor-side trade flow.
- A successful run or well-formed Excel workbook is not evidence of profitable investment performance.

## Recommended implementation documentation checklist

For each page, maintain a verified definition of: (1) source data and timestamp, (2) eligible universe, (3) selection filters, (4) field formulas and units, (5) score weights and thresholds, (6) missing-data handling, (7) sorting and tie-break rules, (8) validation checks, and (9) historical evaluation results, if any.
