# AI-QSIS — Quantitative Stock Intelligence System

> **Repository status:** Private documentation repository. The implementation/source code is intentionally not included.

AI-QSIS is a Python-based quantitative stock research and screening project designed to organize market and company signals into daily research views. It combines technical indicators, relative-strength analysis, sector rotation, volume-derived indicators, and longer-term company-growth metrics to support structured review.

This repository documents the project's purpose, high-level workflow, dependencies, and safe repository practices. It does **not** contain the proprietary implementation, trading logic, or generated market reports.

## Project objectives

- Rank sectors using a collection of market-strength and activity indicators.
- Screen stocks within stronger sectors for further review.
- Separate longer-term business/growth potential from short-term entry timing.
- Organize technical, growth, profitability, valuation, and risk-related signals.
- Produce review-oriented outputs such as spreadsheet summaries and a written report.
- Keep the process reproducible and make its limitations visible.

## High-level capabilities

The current V8 notebook describes these areas:

| Area | Purpose |
|---|---|
| Sector rotation | Ranks sectors and classifies their daily state. |
| Stock screening | Ranks opportunities within selected sectors. |
| Technical analysis | Uses indicators such as moving averages, RSI, MACD, and relative strength. |
| Volume-derived signals | Estimates directional pressure from daily OHLCV candle data. |
| Long-term screening | Combines growth, profitability, technical, and valuation-related measures. |
| Risk and classification | Adds labels intended to support review and prioritization. |
| Reporting | Exports spreadsheet and Word report outputs. |

These descriptions are intentionally high-level. Exact scoring formulas, thresholds, ticker-universe configuration, and source code are not published in this repository.

## Workflow overview

1. Retrieve market and company data from configured data providers.
2. Prepare historical price series and relevant company metrics.
3. Calculate technical, relative-strength, volume-derived, and fundamental indicators.
4. Generate sector and stock rankings.
5. Separate longer-term screening results from daily market/entry-timing signals.
6. Export research outputs for manual review.

Data availability, provider changes, missing history, and symbol coverage can affect results.

## Technology stack

The supplied notebook imports or identifies the following Python packages:

- Python
- `pandas`
- `numpy`
- `yfinance`
- `nsepython`
- `openpyxl`
- `python-docx`

The notebook's stated installation command is:

```bash
pip install yfinance nsepython pandas openpyxl python-docx
```

`numpy` is also imported by the notebook and should be installed explicitly if it is not installed as a dependency.

## Repository contents

This documentation pack is designed to be committed without the implementation.

```text
AI-QSIS/
├── README.md
├── requirements.txt
├── .gitignore
├── SECURITY.md
└── docs/
    ├── PROJECT_OVERVIEW.md
    └── DATA_AND_RISK_NOTES.md
```

## Source code and access policy

- This repository is intended to remain **Private**.
- Do not add the original notebook, Python implementation, private formulas, proprietary configuration, or generated reports unless you deliberately decide they belong in the repository.
- Do not rely on `.gitignore` alone to protect code that has already been staged or committed.
- Before the first push, inspect the staged file list with `git status` and `git diff --cached --name-only`.
- If source code was ever pushed to a public repository, making the repository private later does not undo prior exposure or copies.

## Getting started

This repository is a documentation-only pack and cannot run AI-QSIS by itself. The implementation is maintained separately.

For a local Python environment, the dependency list is provided in `requirements.txt`. Install packages only in the environment used for the private implementation.

## Important limitations

- The project is a research and decision-support tool, not a guaranteed forecasting system.
- A score or label is not a promise of future returns.
- OHLCV data does not directly identify buyer-initiated and seller-initiated trades. The supplied notebook explicitly describes directional-volume measures as estimates based on candle direction and close location.
- Market-data services may have delays, gaps, symbol changes, rate limits, or licensing restrictions.
- Fundamental data fields may be missing or inconsistently reported across companies.
- Historical performance does not guarantee future results.

## Disclaimer

This project is for educational and research purposes only. It is not investment advice, a recommendation to buy or sell any security, or a substitute for independent due diligence. Verify data and assumptions before making any financial decision. You are responsible for complying with applicable laws, market-data provider terms, and exchange rules.

## Project status

The documentation reflects the high-level structure described in the supplied AI-QSIS V8 notebook. It does not claim that the implementation has been independently audited, backtested, or validated for live trading.
