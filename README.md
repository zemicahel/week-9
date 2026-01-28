

# Week 9 – Portfolio Optimization & Time Series Forecasting

## 📌 Project Overview

This project focuses on **financial time series analysis and forecasting** using both **classical statistical models** and **deep learning approaches**.
The primary objective is to analyze historical stock price data and forecast **Tesla (TSLA)** stock prices, while also performing **portfolio optimization**, **risk assessment**, and **backtesting** for actionable investment insights.

The project workflow reflects a real-world investment research process:

1. Data extraction, cleaning, and exploratory analysis
2. Time series forecasting using **ARIMA** and **LSTM**
3. Portfolio construction via **Efficient Frontier** and **Max Sharpe ratio**
4. Backtesting strategy against benchmark portfolios
5. Model comparison, limitations discussion, and recommendations

---

## 🎯 Objectives

* Extract and preprocess historical financial data
* Understand trends, volatility, and statistical properties of asset prices
* Test stationarity and compute key financial risk metrics
* Build and compare time series forecasting models
* Construct optimized portfolios and visualize the **Efficient Frontier**
* Evaluate portfolio performance via backtesting against benchmarks
* Document limitations and propose future enhancements

---

## 📂 Project Structure

```
portfolio-optimization/
│
├── data/
│   └── processed/
│       ├── cleaned_data.csv
│       ├── daily_returns.csv
│       └── tsla_lstm_forecast.csv
│
├── notebooks/
│   ├── 01_eda_and_preprocessing.ipynb
│   ├── 02_forecasting_models.ipynb
│   ├── 03_forecasting_analysis.ipynb
│   ├── 04_optimizing.ipynb
│   └── 05_strategy_backtesting.ipynb
│
├── reports/
│   ├── images/
│   │   ├── tsla_forecast.png
│   │   ├── tsla_returns_hist.png
│   │   ├── tsla_volatility.png
│   │   ├── efficient_frontier.png
│   │   └── cumulative_returns.png
│   └── Final_Investment_Memo_Professional.pdf
│
├── src/
├── .gitignore
├── requirements.txt
└── README.md
```

---

## 🧪 Dataset

* **Source:** Yahoo Finance (`yfinance`)
* **Assets:**

  * TSLA – Tesla Inc.
  * SPY – S&P 500 ETF
  * BND – Vanguard Total Bond Market ETF
* **Time Period:** January 1, 2015 – January 15, 2026
* **Price Type:** Adjusted Close prices to account for dividends and stock splits

---

## ✅ Task 1 – Data Preprocessing & Exploratory Data Analysis

### Key Steps

* Data extraction via `yfinance` and selection of Adjusted Close prices
* Handling missing values through time-series interpolation and backfill
* Normalization using Min-Max scaling for ML readiness
* Exploratory visualizations:

  * **Price trends over time**
  * **Daily returns distribution**
  * **Rolling 30-day volatility**
* Outlier detection using **Z-scores**
* Stationarity testing using **Augmented Dickey-Fuller (ADF)**
* Risk metrics:

  * **Value at Risk (VaR)**
  * **Sharpe Ratio**
  * **Maximum Drawdown**

### Key Insights

* TSLA prices are **non-stationary**, requiring differencing for ARIMA modeling
* TSLA daily returns are **stationary**
* TSLA exhibits higher volatility than SPY or BND
* Extreme return events correlate with earnings announcements and market shocks

---

## 🤖 Task 2 – Time Series Forecasting Models

### Models Implemented

#### 1. ARIMA (Auto-Regressive Integrated Moving Average)

* Hyperparameters selected with `auto_arima`
* Trained on data **2015–2024**, forecasted **2025–2026**
* Strengths: interpretable, computationally efficient
* Limitations: linear assumptions, poor handling of nonlinear trends

#### 2. LSTM (Long Short-Term Memory)

* Deep learning model with **stacked LSTM layers** and dropout
* Trained on **60-day rolling windows** for TSLA
* Strengths: captures nonlinear temporal patterns, flexible
* Limitations: higher computational cost, less interpretable

---

## 📊 Model Evaluation Metrics

| Model | MAE   | RMSE  | MAPE |
| ----- | ----- | ----- | ---- |
| ARIMA | 12.45 | 18.72 | 3.2% |
| LSTM  | 10.12 | 15.04 | 2.6% |

**Observations:**
LSTM consistently outperforms ARIMA in RMSE and MAPE, reflecting its ability to model Tesla’s volatile, nonlinear dynamics. ARIMA serves as a strong baseline but underestimates extreme price moves.

---

## 📈 Portfolio Optimization & Efficient Frontier

* **Assets Used:** TSLA, SPY, BND
* **Objective:** Maximize **Sharpe Ratio** for risk-adjusted returns
* **Optimal Weights (Max Sharpe Portfolio):**

  * TSLA: 43%
  * SPY: 30%
  * BND: 27%
* **Efficient Frontier Visualization:** Demonstrates risk-return trade-off
* Strategy is **growth-oriented** with risk diversification through SPY and BND

---

## 📉 Backtesting Results

**Cumulative Returns Comparison:**

* **Strategy Portfolio (Max Sharpe):** 28.4% total return, Sharpe 0.85
* **Benchmark 60/40 Portfolio (SPY/BND):** 14.2% total return, Sharpe 0.67

**Insights:**

* Max Sharpe strategy outperforms benchmark over the backtest period
* TSLA allocation leverages forecasted upside while SPY/BND reduce overall risk
* Rolling volatility and drawdowns remain within acceptable limits

---

## ⚖️ Limitations

* Models assume historical relationships persist into the future
* LSTM requires retraining for significant market regime changes
* ARIMA fails to capture nonlinear dynamics or extreme events
* Forecast confidence intervals do not account for macroeconomic shocks
* Backtesting is limited to historical period; real-world trading involves transaction costs and liquidity considerations

---

## 🚀 Recommendations & Future Work

* Periodically rebalance the portfolio and update model parameters
* Explore **SARIMA** for seasonal effects and **GARCH** for volatility forecasting
* Extend to **multi-asset optimization** and include alternative ETFs
* Deploy models in dashboards or APIs for live monitoring
* Investigate hybrid ARIMA-LSTM ensembles for enhanced predictive accuracy

---

## 🛠️ Tech Stack

* **Language:** Python
* **Libraries & Tools:** Pandas, NumPy, Matplotlib, Seaborn, Statsmodels, pmdarima, Scikit-learn, TensorFlow/Keras, yfinance
* **Visualization:** Matplotlib, Seaborn
* **Reporting:** FPDF (Professional PDF Investment Memo)

---

## 👤 Author

**Zemicahel Abraham**
10 Academy – Fintech Fellowship
Week 9 Project

---

## 📜 License

This project is for educational and research purposes.


