#  **README — Nikkei 225 Stochastic Modeling & Option Pricing Project**

## **Overview**

This project analyzes the stochastic behavior of the Nikkei 225 index and evaluates option mispricing and trading strategies using quantitative finance techniques.
It combines **GBM modeling**, **volatility smile analysis**, and **Monte Carlo backtesting** to examine tail risk and extract tradable signals from option skew.

<img width="509" height="222" alt="image" src="https://github.com/user-attachments/assets/82b7d33d-37f9-4ef2-9de3-e282871040bf" />

---

##  **1. Stochastic Modeling of the Nikkei 225**

Using daily price data (Jan 4, 2022 – Present), the index is modeled with **Geometric Brownian Motion (GBM)**.

### **Estimated Parameters (MLE)**

* **Drift (μ): 0.00044 per day**
* **Volatility (σ): 0.01223 per day**

### **Key Findings**

* Log-returns exhibit a **heavy left tail**, indicating elevated crash risk not captured by GBM.
* A **10% OTM put hedge** significantly reduces downside risk.

### **Backtest Results (Hedge Effectiveness)**

| Metric     | Unhedged | Hedged (10% OTM put) | Improvement             |
| ---------- | -------- | -------------------- | ----------------------- |
| Worst PnL  | –18,700  | –4,300               | **+77% reduction**      |
| 5% VaR     | –12,400  | –2,100               | **+83% improvement**    |
| Median PnL | 5,800    | 3,900                | Lower due to hedge cost |

---

##  **2. Option Pricing & Volatility Smile Analysis**

Nikkei 225 index options were priced using **Black–Scholes and Newton–Raphson IV calibration**.

### **Key Findings**

* Strong **downside skew** detected:

  * **45% IV** on low-strike puts
  * **23.6% IV** ATM
* Deep ITM calls showed **7–9% overpricing**.

---

## 📈 **3. Skew-Extraction Trading Strategy**

Based on the volatility smile:

### **Strategy Construction**

* **Short deep ITM calls** (overpriced)
* **Long OTM calls** (cheap convexity)
* **Short low-strike puts** (high crash premia)

### **Monte Carlo Backtest (100,000 paths)**

* **Expected annual return:** **20.4%**
* **Sharpe ratio:** **0.47**
* Confirms profitability of monetizing volatility skew.

---

##  **Summary**

This project shows that:

* The Nikkei 225 exhibits **significant tail risk**
* Downside insurance (OTM puts) is **extremely expensive**
* Volatility skew provides **systematic arbitrage opportunities**
* A skew-extraction strategy can achieve **20% annual expected return**

It demonstrates an end-to-end application of **stochastic modeling, option pricing, and trading strategy backtesting**.
