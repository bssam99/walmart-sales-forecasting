# 📊 Walmart Sales Forecasting Project

This project analyzes and forecasts Walmart's weekly sales for a specific store (Store 1) using Time Series Analysis techniques, including Auto-ARIMA modeling.

---

## 📁 Project Structure

- `walmart_sales_forecasting.ipynb` — Main Jupyter Notebook containing all data analysis and forecasting steps.
- `walmart_report.html` — Automated EDA report for walmart data generated using Sweetviz.
-  `sales1_report.html` — Automated EDA report for walmart store1 generated using Sweetviz.
- `README.md` — Project documentation (you are here!).

---

## 🛠️ Tools and Libraries Used

- **Pandas** — Data manipulation
- **NumPy** — Numerical computations
- **Matplotlib & Seaborn** — Data visualization
- **Statsmodels** — Statistical tests and plots
- **pmdarima** — Auto-ARIMA model
- **scikit-learn** — Preprocessing and error metrics
- **Sweetviz** — Automated EDA reporting

---

## 🚀 Project Workflow

1. **Data Loading:**\
   Load the Walmart sales dataset and explore its basic characteristics.

2. **Preprocessing:**

   - Convert the 'Date' column to datetime format.
   - Sort data chronologically.
   - Filter data for Store 1.
   - Set 'Date' as the index.

3. **Exploratory Data Analysis (EDA):**

   - Visualize sales over time.
   - Check for stationarity using the Augmented Dickey-Fuller (ADF) Test.
   - Analyze seasonality using ACF/PACF plots and seasonal decomposition.

4. **Data Scaling:**\
   Normalize the sales data using `StandardScaler` to improve model performance.

5. **Model Building (Auto-ARIMA):**

   - Fit an Auto-ARIMA model on the training data (80% split).
   - Forecast the next 24 weeks.

6. **Inverse Scaling and Visualization:**

   - Inverse transform predictions to original scale.
   - Plot predictions vs actual sales.

7. **Model Evaluation:**

   - Evaluate using Mean Absolute Error (MAE) and Root Mean Squared Error (RMSE).
   - Compare with the average sales to assess error significance.

8. **Automated EDA Report:**

   - Generate a detailed EDA report using Sweetviz.

---

## 📈 Results

- **Mean Absolute Error (MAE):** \~ 49,842.77
- **Root Mean Squared Error (RMSE):** \~ 62,893.81
- **Average Weekly Sales:** \~ 1,555,264

Despite a relatively high RMSE, the model shows reasonable performance given the scale of sales values.

---

## 📋 Future Improvements

- Experiment with SARIMA and Prophet models for possibly better accuracy.
- Incorporate exogenous variables (e.g., promotions, holidays) into the forecasting model.
- Hyperparameter tuning using manual grid search for better model optimization.

---

## ✨ Author

- **Bssam Ahmed** — [GitHub Profile](https://github.com/bssam99)
