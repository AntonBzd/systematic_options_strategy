# 📈 Systematic Options Strategy

This repository contains a **quantitative trading strategy** for options, inspired by academic research on **momentum patterns in options markets**. The strategy is designed to predict intraday **high and low returns of straddles** based on the previous day's returns in the same time window.

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
- Fetches **intraday stock and options data**.
- Computes **straddle returns** over a 30-minute window.
- Runs **cross-sectional regressions** to determine if yesterday's return influences today's return.
- Constructs a **momentum portfolio**:
  - **Long** on the top-performing options.
  - **Short** on the worst-performing options.

### 2️⃣ **Live Paper Trading (`Intraday_Option_Return_Paper_Trading.ipynb`)**
- Uses **IBKR API (`ib_insync`)** to fetch **real-time market data**.
- **Places market orders** at the next trading session open.
- Continuously **updates the portfolio** based on the strategy signals.
- **Monitors performance metrics** and logs trades.

---

## 📚 Dependencies

To install required libraries:

```bash
pip install ib_insync pandas numpy scipy yfinance matplotlib statsmodels nest_asyncio
```

---

## 🔥 Author & Contact
👤 **Antonin Bezard**  
📧 Reach me via [LinkedIn](https://www.linkedin.com/in/antonin-bezard-a11511177/)

---
