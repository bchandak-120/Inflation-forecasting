# Forecasting U.S. Inflation: A Comparative Out-of-Sample Study

A single Jupyter notebook that compares five inflation-forecasting models on live FRED data using a strict rolling-origin walk-forward backtest.

## What's inside

- `Inflation_Forecasting_Bhavesh_Chandak.ipynb` — fully annotated, runnable notebook with all outputs embedded.

## Models compared

1. Random Walk (Atkeson-Ohanian benchmark)
2. AR(12) — direct multi-step OLS on 12 lags
3. ARIMA(2,0,2) — iterated Box-Jenkins forecast
4. Phillips curve — inflation lags + unemployment + oil-price growth
5. Multivariate — adds rates, term spread, IP growth, payrolls, PPI

## Data

Nine monthly U.S. macro series pulled at runtime from the public FRED CSV endpoint (no API key required): `CPIAUCSL`, `PCEPI`, `PPIACO`, `UNRATE`, `INDPRO`, `PAYEMS`, `FEDFUNDS`, `DGS10`, `DCOILWTICO`.

## How to run

```bash
pip install pandas numpy matplotlib statsmodels requests jupyter
jupyter notebook Inflation_Forecasting_Bhavesh_Chandak.ipynb
```

Then Cell -> Run All. The walk-forward backtest takes roughly 1-3 minutes. An internet connection is required to download the FRED series. The notebook also auto-installs any missing packages on first run.

## Structure

- **Part 1 — Setup.** Imports, data loaders, feature construction, forecasting models, and evaluation helpers.
- **Part 2 — Run the Analysis.** Downloads data, builds features, runs the rolling-origin backtest for CPI and PCE.
- **Part 3 — Outputs.** Data summary, inflation chart, RMSE/MAE tables (full + pre-2020 + post-2020), predicted-vs-actual plots at h=1 and h=12, RMSE bar chart, PCE robustness table.
- **Results and Discussion + Conclusion.**
