# Sector Rotation and V8 Opportunity Views

This page covers the sector-oriented workbook views: **VB Sector Rotation**, **VB Booming**, and **VB Best Sector Stocks**.

## VB Sector Rotation

### Purpose

Rank sectors using the sector fields shown in the workbook, including multiple return horizons, buying-related scores, volume surge, breadth, and price/technical confirmation measures.

### Fields

- `SectorRank`, `Sector`, `SectorScore`, `DailyState`, `Stocks`
- `Avg1DReturn`, `Avg5DReturn`, `Avg20DReturn`
- `BuyingPressureScore`, `VolumeSurgeScore`, `BuyingBreadthPct`
- `PriceConfirmationScore`, `TechnicalConfirmationScore`
- `AvgBuyVolumePct`, `AvgSellVolumePct`, `AvgBuySellRatio`, `AvgVolumeRatio`

The return horizons help the reader compare short-term and multi-day behaviour. Breadth can help distinguish a sector move supported by more stocks from one driven by a small number of names, depending on the implementation's definition. Volume and confirmation fields add context but must be interpreted using the actual formulas.

### Reading `DailyState`

The observed output includes labels such as `BOOMING – STRONG BUYING`, `LEADING – BUYING`, `EMERGING BUYING`, and `WATCH`. The exact state thresholds and precedence rules should be documented from source code. A label is a system classification, not a forecast.

## VB Booming

The supplied column list is the same as VB Sector Rotation. This suggests that the page provides a selected subset or focused view, but its exact inclusion rules must be confirmed. Document the actual filters, score thresholds and sort order rather than assuming the tab simply filters on a particular `DailyState`.

## VB Best Sector Stocks

This view combines the broad All Stocks schema with sector and V8-specific fields:

- `OpportunityRank`, `SectorScore`
- `NetBuyingPressurePct`, `LiveBuyingScore`, `LiveBuyingSignal`
- `V8_OpportunityScore`, `V8_Opportunity`, `UniverseStatus`

It can be read as a bridge between sector context and stock-level research: first inspect the sector's relative state, then review the stock's price, volume, technical, fundamental and risk fields.

## Example interpretation

In the supplied console output, Textiles appears at the top of the displayed sector ranking with a `SectorScore` of 83.01 and the state `BOOMING – STRONG BUYING`. The accompanying stock-opportunity output displays LIBAS, NHPC and KIRLPNu among its leading rows. These examples demonstrate the format of a run, not enduring recommendations or proof that the signals predict future returns.

## Important caveats

- Sector rankings depend on the universe of stocks assigned to each sector and the available data.
- Sector-level averages can hide dispersion among individual companies.
- `AvgBuyVolumePct` and related directional measures may be estimates if derived from OHLCV candles.
- `LiveBuyingScore` and `LiveBuyingSignal` do not prove real-time data unless timestamps and refresh behaviour confirm it.
- Verify the formulas and selection rules before describing the views as a validated strategy.
