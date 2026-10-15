# Walmart Weekly Sales Forecasting

Forecasting 24 weeks of Walmart store sales with a **seasonal ARIMA** model, using a full time-series workflow: stationarity testing, seasonality analysis, automated order selection and back-testing on held-out weeks.

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)
![statsmodels](https://img.shields.io/badge/statsmodels-4051B5)
![pmdarima](https://img.shields.io/badge/pmdarima-Auto--ARIMA-2E7D32)

## Results

Forecast for Store 1, 24 weeks ahead, compared with the actual sales:

| Metric | Value |
|---|---:|
| MAPE | **3.14%** |
| MAE | $49,843 |
| RMSE | $62,894 |
| Average weekly sales | ~$1.56M |

Selected model: **SARIMA(0,1,2)(1,0,0)[52]** – the seasonal term captures the yearly (52-week) holiday cycle.

## Approach

1. **Preprocessing** – parsed dates, sorted chronologically and isolated Store 1 (143 weeks, Feb 2010 – Oct 2012).
2. **Stationarity** – Augmented Dickey-Fuller test (ADF = −5.10, p < 0.001).
3. **Seasonality** – ACF plot and additive seasonal decomposition show a strong yearly pattern around the holidays.
4. **Modeling** – `pmdarima.auto_arima` with a stepwise search over seasonal ARIMA orders (m = 52), trained on the first 80% of weeks.
5. **Evaluation** – 24-week forecast converted back to dollars and scored against the actual sales (MAE, RMSE, MAPE).
6. **Automated EDA** – Sweetviz reports for all 45 stores and for Store 1 (in `reports/`).

## Project Structure

```text
├── walmart_sales_forecasting.ipynb   # analysis + forecasting
├── data/
│   └── walmart_sales.csv             # 6,435 weekly records, 45 stores
├── reports/
│   ├── eda_all_stores.html           # Sweetviz report, all stores
│   └── eda_store1.html               # Sweetviz report, Store 1
├── requirements.txt
└── README.md
```

## How to Run

```bash
git clone https://github.com/bssam99/walmart-sales-forecasting.git
cd walmart-sales-forecasting
pip install -r requirements.txt
jupyter notebook walmart_sales_forecasting.ipynb
```

Download the `.html` files in `reports/` and open them in a browser to explore the EDA reports.

## Next Steps

- Fit the scaler on the training weeks only, and add rolling-origin (walk-forward) validation.
- Add exogenous variables already in the data (holiday flag, temperature, fuel price, CPI, unemployment) with SARIMAX.
- Compare with Prophet and gradient-boosted models across all 45 stores.

## Author

**Bssam Ahmed** · [LinkedIn](https://www.linkedin.com/in/bssam-ahmed) · [GitHub](https://github.com/bssam99)
