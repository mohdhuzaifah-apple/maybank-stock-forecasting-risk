# Maybank Stock Price Forecasting & Risk Analysis

**Python | Time Series Analysis | ARIMA | Financial Risk | Monte Carlo Simulation**

## Project Overview

This project analyses historical stock prices of **Malayan Banking Berhad (Maybank, 1155.KL)** using Python, with a focus on time-series forecasting and financial risk analysis.

The project aims to:

1. Explore historical Maybank stock price trends.
2. Evaluate the forecasting performance of an ARIMA model.
3. Assess financial risk using volatility, Value-at-Risk (VaR), Conditional Value-at-Risk (CVaR), and Monte Carlo simulation.

**Data Source:** Yahoo Finance  
**Study Period:** January 2021 – November 2026  
**Dataset:** 1,440 historical stock records

## Tools & Technologies

- **Programming:** Python
- **Libraries:** Pandas, NumPy, Matplotlib, Statsmodels, yfinance
- **Environment:** Jupyter Notebook
- **Techniques:** Exploratory Data Analysis, ARIMA Forecasting, Model Evaluation, Financial Risk Analysis, Monte Carlo Simulation

## Methodology

The project followed five main stages:

**1. Data Collection and Exploration**

Downloaded historical Maybank stock prices from Yahoo Finance and examined price movements using 20-day and 50-day moving averages.

**2. Stationarity Testing**

Applied the Augmented Dickey-Fuller (ADF) test to log closing prices and their first differences. The results supported first differencing for ARIMA modelling.

**3. ARIMA Forecasting and Evaluation**

Developed an ARIMA(1,1,1) model, performed chronological train-test validation, and compared forecasting accuracy against a simple benchmark using RMSE.

**4. Financial Risk Analysis**

Calculated annualised volatility, historical VaR, and CVaR to evaluate return fluctuations and downside risk.

**5. Monte Carlo Simulation**

Simulated 1,000 possible price paths by resampling historical daily log returns, exploring the distribution of potential outcomes over 30 trading observations.

## Visualisations

The analysis includes five charts:

### Historical Stock Price Trends

![Maybank Historical Price Trends](outputs/maybank_price_trend.png)

Shows Maybank's historical closing prices alongside 20-day and 50-day moving averages.

### ARIMA Forecast Evaluation

![ARIMA Forecast Evaluation](outputs/maybank_arima_forecast.png)

Compares actual testing-period prices against ARIMA forecasts and the constant-price benchmark.

### Financial Risk Distribution

![Maybank Daily Return Distribution](outputs/maybank_risk_distribution.png)

Illustrates the distribution of historical daily returns and the 95% VaR threshold.

### Monte Carlo Simulation

![Maybank Monte Carlo Simulation](outputs/maybank_monte_carlo.png)

Displays simulated price paths and percentile-based scenarios.

### Future ARIMA Forecast

![Maybank Future Price Forecast](outputs/maybank_future_forecast.png)

Shows the 30-observation ARIMA central forecast and its 95% prediction interval.

## How to Run

1. Download or clone this repository.
2. Open the project folder using Jupyter Notebook or JupyterLab.
3. Install dependencies using `pip install -r requirements.txt`.
4. Open `maybank_analysis.ipynb`.
5. Run the notebook cells in sequence.

An internet connection is required to download historical market data through Yahoo Finance. Results may change if the downloaded data are updated or revised.

## Key Findings

### 1. Stock Price Forecasting

An ARIMA(1,1,1) model was developed using historical Maybank closing prices. The dataset was divided chronologically into 90% training data and 10% testing data.

The model was evaluated using Root Mean Squared Error (RMSE) and compared against a constant-price benchmark.

| Model | RMSE |
|---|---:|
| ARIMA(1,1,1) | RM0.8620 |
| Constant-Price Benchmark | RM0.8924 |

**Result:** The ARIMA model achieved approximately **3.4% lower RMSE** than the benchmark.

Although ARIMA performed slightly better, both approaches struggled to capture the sustained stock price decline during the testing period.

### 2. Financial Risk Analysis

Historical daily returns were analysed using adjusted closing prices.

| Risk Measure | Result |
|---|---:|
| Annualised Volatility | 12.33% |
| 95% Daily Value-at-Risk | 1.12% |
| 95% Daily Conditional VaR | 1.73% |

**Result:** Historical VaR indicates that losses exceeded approximately 1.12% on the worst 5% of trading days, while CVaR indicates an average loss of 1.73% within that group.

These measures help quantify historical downside exposure.

### 3. Future Price Forecasting

The ARIMA model was retrained using all available historical closing-price observations to generate a forecast over the next 30 trading observations.

| Forecast Measure | Result |
|---|---:|
| Last Closing Price | RM9.87 |
| Day 30 ARIMA Forecast | RM9.89 |
| Day 30 Lower Prediction Limit | RM9.28 |
| Day 30 Upper Prediction Limit | RM10.54 |

**Result:** The ARIMA central forecast remained relatively stable, while the 95% prediction interval widened over time, reflecting increasing forecast uncertainty.

### 4. Monte Carlo Simulation

A historical-bootstrap Monte Carlo simulation was conducted using **1,000 simulated price paths over 30 trading observations**.

| Scenario | Simulated Ending Price |
|---|---:|
| 5th Percentile | RM9.32 |
| Median | RM9.96 |
| 95th Percentile | RM10.69 |

**Result:** The simulations generated a range of potential future price outcomes, illustrating uncertainty and possible downside exposure.

The simulation results represent statistical scenarios rather than guaranteed future stock prices.

## Conclusion

This project demonstrates the application of Python in financial data analysis, time-series forecasting, and quantitative risk assessment.

The ARIMA model achieved slightly lower forecasting errors than the selected benchmark, while the risk analysis and Monte Carlo simulations provided additional insight into historical losses and possible future outcomes.

**Key Takeaway:** Financial forecasting should be evaluated alongside risk analysis, as historical patterns do not guarantee future price movements.

## Limitations

- The analysis focuses on one stock and one testing period.
- ARIMA(1,1,1) was selected as a simple starting model rather than through exhaustive model selection.
- The forecast comparison uses a fixed-origin evaluation.
- Historical-bootstrap simulation assumes independently sampled historical returns.
- ARIMA uses unadjusted closing prices, whereas risk analysis and Monte Carlo simulation use adjusted closing prices.
- Unexpected market events may produce outcomes outside the estimated forecast ranges.

**Disclaimer:** This project is for educational and analytical purposes only and does not constitute investment advice.
