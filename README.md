# Stock Return Prediction Model with Reddit Sentiment Analysis

## Executive Summary
**Objective:** Develop a machine learning model to enhance trade execution by predicting stock returns using Reddit sentiment data.  

**Key Innovation:** Combines 12M+ Reddit comments with 2.4M+ historical returns to generate actionable trading signals.

---

## Methodology

### 1. Data Preparation
- **Sources:** 
  - 2.4M rows of 1-day returns (3,500 tickers)
  - 12M rows of Reddit sentiment data
- **Preprocessing:**
  - Normalized percentages → decimals
  - Standardized timestamps to EST
  - Mapped after-hours/weekend comments to next trading day
  - Merged datasets by `(date, ticker)` pairs

### 2. Feature Engineering
**14 custom features** designed to capture sentiment dynamics:
- **Lag Effects:** 1-day to 5-day sentiment persistence  
- **Momentum Indicators:** 3/7/21-day sentiment trends  
- **Volume Metrics:** 3/7/14-day avg. sentiment & comment counts  

### 3. Model Selection
**Ridge Regression (L2 Regularization)**  
- **Optimal hyperparameter:** `alpha=0.01` (validated against 10, 1, 0.01)  
- **Advantage:** Penalizes noisy features while maintaining OLS interpretability  

---

## Results
| Metric               | Value    | Interpretation          |
|----------------------|----------|-------------------------|
| RMSD                 | 4.2%     | Predictions ±4.2% error |
| R²                   | -0.1435  | Baseline outperforms    |
| Avg. Annual Return   | -7.32%   | Needs improvement      |
| Annualized Volatility| 6.72%    | **Observed low volatility**    |
| Sharpe Ratio         | -1.13    | Low risk, negative return |

**Key Insight:** While returns were suboptimal, the model achieved **historically low volatility** (6.72% vs S&P’s 10–20%), providing a foundation for refinement.

---

## Next Steps
1. **Expand Data Sources:** Incorporate market-wide sentiment (Twitter, news)  
2. **Test Alternative Models:**  
   - Gradient Boosting (XGBoost) for nonlinear relationships  
   - LSTM networks for temporal patterns  
3. **Enhance Features:**  
   - Sector-specific sentiment weights  
   - Earnings call alignment  

---


![group2_cumulative_returns](https://github.com/user-attachments/assets/9836ca9c-3b36-45b4-ad62-aa46fbbf1c48)

![group2_longshort_returns](https://github.com/user-attachments/assets/373f34ea-c7af-4757-9d8a-6cb19187cf9d)

![group2_performance_summary](https://github.com/user-attachments/assets/2bdaf537-30da-4707-8f1b-cb0d549d48d0)

![group2_regression_metrics](https://github.com/user-attachments/assets/5b10592d-f424-4767-8003-4e882d4c9ca5)
