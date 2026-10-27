# AI-QSIS Project Overview

## Purpose

AI-QSIS (Quantitative Stock Intelligence System) is intended to provide structured daily stock-research views and longer-term screening summaries.

## Functional areas described by the current notebook

### 1. Market and sector view
Ranks sectors and assigns a daily state intended to describe relative sector strength or weakness.

### 2. Stock opportunity screening
Ranks stocks associated with the sector view and presents technical and volume-derived indicators for additional review.

### 3. Technical indicators
The notebook includes calculations or use of indicators such as:
- Relative Strength Index (RSI)
- Moving averages
- Moving Average Convergence Divergence (MACD)
- Relative strength against a benchmark
- Volume comparisons

### 4. Long-term screening
The notebook separates business/growth potential from entry timing and includes measures or labels related to:
- Revenue and earnings growth
- Growth acceleration
- Profitability trajectory and margin expansion
- Technical score
- Valuation score
- Growth stage and risk level
- Long-term view and recommendation-style classification

### 5. Outputs
The notebook describes generating an Excel workbook and a Word report in an output directory. These generated artifacts are deliberately excluded from this documentation pack.

## Data inputs and dependencies

The notebook imports `nsepython`, `yfinance`, `pandas`, `numpy`, `openpyxl`, and `python-docx`. It describes using historical price data and company metrics. Data access and coverage depend on the relevant providers and available symbols.

## Execution boundary

This document is an architectural summary, not an implementation guide. It intentionally omits exact formulas, thresholds, ticker lists, internal functions, and source code.

## Validation still required

Before relying on the system for consequential decisions, independently validate data quality, score behavior, missing-data handling, look-ahead bias, survivorship bias, transaction costs, liquidity, slippage, and out-of-sample performance. No such validation is asserted by this overview.
