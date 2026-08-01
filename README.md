# Sentiment-Driven Crude Oil Price Impact Analysis

Summer research internship project at **NIT Calicut**, under the guidance of **Dr. Anu Mary Chacko**.

## Overview

This project investigates whether news sentiment carries measurable information about crude oil price movements, and — more specifically — whether that relationship is concentrated around geopolitical events rather than being constant over time.

## Data

- **News headlines:** ~34,272 deduplicated headlines (2020–2026), scraped from OilPrice.com, Investing.com (via `cloudscraper`), and Hellenic Shipping News
- **Price data:** WTI and Brent crude, 1,663 trading days
- **Structured event signal:** GDELT, used as a complementary indicator alongside headline sentiment

## Methodology

1. **Web scraping** — headline collection and deduplication across three sources
2. **Sentiment scoring** — dual approach using NLTK VADER (lexicon-based) and ProsusAI/FinBERT (transformer-based, finance-tuned)
3. **Stationarity testing** — Augmented Dickey-Fuller (ADF) checks on price series
4. **Correlation analysis** — Pearson correlation between sentiment and price at lags 0, 1, 3, and 7 days
5. **Granger causality testing** — FinBERT sentiment showed significance at lags 4–7; VADER sentiment was not significant
6. **Regime segmentation** — splitting the sample by volatility regime and by ±7-day windows around major geopolitical events
7. **Forecasting / impact modeling** — *(see Results — final modeling approach below)*

## Key Findings

- FinBERT (transformer-based) sentiment outperformed VADER (lexicon-based) as a predictive signal, showing Granger causality at longer lags (4–7 days)
- Sentiment's relationship with price is **not constant** — it strengthens meaningfully during geopolitical event windows and is weak-to-absent during calmer periods
- This event-conditional pattern suggests sentiment acts as an amplifier of price response during shocks, rather than a standalone driver in normal market conditions

> **Note:** This section covers the confirmed pipeline. The final forecasting/statistical modeling step in this repo may differ from earlier drafts — update this section with the specific model and results you used in the final submission.

## Repository Structure

```
├── notebooks/          # Analysis notebooks
├── scripts/            # Scraping, sentiment scoring, analysis scripts
├── presentation/        # Final project presentation
├── outputs/             # Charts, figures, result exports
└── README.md
```

## Tools & Libraries

`Python` · `cloudscraper` · `NLTK (VADER)` · `transformers (FinBERT)` · `pandas` · `statsmodels` (ADF, Granger causality) · `matplotlib` / `seaborn`

## Author

Nishwan — MSc Computer Science (Big Data Analytics)
