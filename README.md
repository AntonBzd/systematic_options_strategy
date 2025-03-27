# 📈 Systematic Options Strategy

This repository contains a **quantitative trading strategy** for options, inspired by academic research on **momentum patterns in options markets**. The strategy is designed to build an intraday portfolio from **high and low returns of straddles** based on the previous day's returns in the same time window.

It includes:
- **Historical Data Processing** (`Intraday_Option_Return_Historical_Data.ipynb`): Fetches and analyzes historical intraday returns of options.
- **Paper Trading Implementation** (`Intraday_Option_Return_Paper_Trading.ipynb`): Deploys the strategy in a **live paper trading environment** using IBKR API.

---

## 🚀 Features

- 📡 **Intraday options return analysis** using historical data.
- 📊 **Cross-sectional regressions** to detect autocorrelation in option returns.
- ⚡ **Automated portfolio construction** based on options return signals.
- 🏦 **Live market data fetching** via **Interactive Brokers API**.
- 📈 **Paper trading execution** with real-time order placement.

---

## 📂 Repository Structure

```
📁 Systematic Options Strategy
│── 📄 README.md
│── 📓 Intraday_Option_Return_Historical_Data.ipynb  # Historical backtesting
│── 📓 Intraday_Option_Return_Paper_Trading.ipynb    # Live paper trading setup
```

---

## 📜 Strategy Breakdown

### 1️⃣ **Historical Data Analysis (`Intraday_Option_Return_Historical_Data.ipynb`)**
This script **retrieves historical stock and option price data** to analyze **intraday straddle returns**. It follows these key steps:

#### 🔹 **Fetching Historical Data**
- Uses **Interactive Brokers (`ib_insync`) API** to fetch **1-minute stock price data** for **S&P 500 stocks**.
- Filters **30-minute time slots** (e.g., 9:35 AM, 10:00 AM, etc.) to compute intraday returns.

#### 🔹 **Calculating Straddle Returns**
- Retrieves **at-the-money (ATM) options** with expirations between **30 to 180 days**.
- Fetches **intraday call and put option prices** every **30-minute time slots**.
- Computes **log-returns of straddles** based on the price difference.

#### 🔹 **Cross-Sectional Regression Analysis**
- Runs a **cross-sectional regression** to measure if **yesterday’s return** influences today’s return.
- Plots the **gamma coefficient** and **T-statistics** to validate the return persistence.

#### 🔹 **Backtesting a High-Low Portfolio**
- Constructs a **long-short portfolio** based on momentum:
  - **Long** on options with the highest past performance.
  - **Short** on the worst-performing options.
- Computes **cumulative returns** for each **30-minute period** and **plots Sharpe ratios** to identify the best trading windows.



### 2️⃣ **Live Paper Trading (`Intraday_Option_Return_Paper_Trading.ipynb`)**
This script implements the **live execution** of the strategy in **Interactive Brokers’ Paper Trading** environment.

#### 🔹 **Fetching Real-Time Market Data**
- Uses **IBKR API** to get **stock prices at 9:35 AM**.
- Retrieves **ATM options data** for the **most liquid S&P 500 stocks**.

#### 🔹 **Placing Trades**
- **Ranks stocks based on previous-day straddle returns**.
- Buys **long straddles** for the **top quantile** (Q5).
- Sells **short straddles** for the **bottom quantile** (Q1).

#### 🔹 **Closing Positions**
- **Closes all positions at 10:00 AM** (after 25 minutes of holding).

#### 🔹 **Monitoring PnL**
- Retrieves **realized and unrealized PnL** at both:
  - **Account Level**
  - **Position Level** (for each ticker)

---

## 📚 Dependencies

- Install Interactive Brokers Gateway (10.30 version)
- Install Ngrok for the API Gateaway
- To install required libraries on Google Colab:
```bash
!pip install ib_insync pandas numpy scipy yfinance matplotlib statsmodels nest_asyncio
```

---


## 📚 References

This strategy is inspired by the academic paper:

- **"Intraday Option Return: A Tale of Two Momentum"** (16 Dec 2024)  
  *Authors:* Zhi Da, Ruslan Goyenko, and Chengyu Zhang. 
  📄 [Read the paper here](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5018430)

The paper explores **short-term momentum in option prices**, revealing **predictability in intraday returns**.

---


## 🔥 Author & Contact
👤 **Antonin Bezard**  
📧 Reach me via [LinkedIn](https://www.linkedin.com/in/antonin-bezard-a11511177/)

---
