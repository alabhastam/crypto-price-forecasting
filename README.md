# 📊 Cryptocurrency Price Prediction (2020–2025)

A machine learning project analyzing and predicting cryptocurrency prices using historical market data for the Top 100 cryptocurrencies from 2020 to 2025.

---

## 📌 Project Overview
This project explores **cryptocurrency market trends** and applies **machine learning models** to predict next-day prices.  
Data preprocessing, feature engineering, and multiple regression models are benchmarked to evaluate predictive power.

---

## 📂 Dataset
**Source**: Kaggle – *Top 100 Cryptocurrency (2020–2025)*  
**Columns**:
- `symbol` – Coin ticker (e.g., BTCUSDT)
- `date` – Trading date
- `open`, `high`, `low`, `close` – OHLC prices
- `network` – Blockchain network classification
- Engineered Features:
  - `return`, `btc_return`, `excess_return`
  - Rolling volatility & moving averages (7d, 30d)
  - RSI (14-day)
  - `coin_age` – Time since coin’s first appearance  
- `target` – Next day’s closing price (prediction target)

---

## ⚙️ Methodology

### 1. Data Preprocessing
- Converted date column to datetime format.
- Removed text columns from feature set to avoid model errors.
- Removed `close` and `target` from features to prevent **data leakage**.
- Dropped NaN rows arising from rolling window features.

### 2. Feature Engineering
- Daily returns & excess returns over Bitcoin.
- 7‑day & 30‑day rolling volatility and moving averages.
- Relative Strength Index (RSI) over a 14‑day window.
- Coin age calculation in days.

### 3. Modeling & Benchmarking
Baseline regression models tested:
- **Linear Regression**
- **Random Forest**
- **XGBoost**
- **LightGBM**
- **CatBoost**

**Evaluation Metrics**:
- RMSE (Root Mean Squared Error)
- MAE (Mean Absolute Error)
- R² (Coefficient of Determination)

---

## 📈 Results (Clean Benchmark, No Leakage)

| Model            |   RMSE   |   MAE   |   R²     |
|------------------|----------|---------|----------|
| LinearRegression | 0.500103 | 0.499690 | -0.000524 |
| CatBoost         | 0.502219 | 0.497938 | -0.009011 |
| RandomForest     | 0.503608 | 0.500304 | -0.014600 |
| XGBoost          | 0.505842 | 0.496087 | -0.023622 |
| LightGBM         | 0.512249 | 0.497788 | -0.049715 |

> ℹ️ Negative R² values indicate that models did not outperform a simple mean predictor with the current features.

---

## 🚀 Next Steps
- **Feature enrichment**:
  - Additional lags and technical indicators (MACD, Bollinger Bands, etc.)
  - Market sentiment from social media/news
- **Model tuning**:
  - Hyperparameter optimization (LightGBM, XGBoost, CatBoost)
  - Time-series cross-validation (walk-forward validation)
- **Deployment**:
  - Streamlit dashboard for real-time inference

---

## 🛠️ Technologies Used
- **Python**: pandas, numpy, matplotlib, seaborn
- **ML**: scikit-learn, XGBoost, LightGBM, CatBoost
- **EDA**: matplotlib & seaborn visualizations
- **Version Control**: Git, GitHub

---

## 📜 License
This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## 🙌 Acknowledgements
- Kaggle dataset: *Top 100 Cryptocurrency (2020–2025)*  
- Open-source ML libraries and the Python data community
