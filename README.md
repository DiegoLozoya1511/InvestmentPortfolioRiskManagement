# Investment Portfolio Risk Management

This project builds and evaluates a multi-asset investment portfolio under a **moderate risk** investor profile, focusing on **risk-aware asset allocation**, **portfolio optimization**, and **comparative backtesting** against a market benchmark.

## Project Overview

### 1) Asset selection (qualitative + macro outlook)
Assets were selected based on an economic outlook assessment and diversification goals. The portfolio construction includes exposure to different economic roles (offensive vs defensive assets) and a diversifier (gold).

### 2) Data acquisition
Historical market data is used to build the analysis:
- **Prices and volumes** for the selected assets
- A **benchmark** (market index proxy) used as the reference portfolio for comparison

From prices, **daily returns** are computed and used to estimate risk/return statistics (e.g., expected return, volatility, correlations/covariance).

## Portfolio Construction & Optimization

Four allocation methodologies were implemented and compared:

1. **Minimum Variance (Min-Var)**
   - Finds weights that minimize portfolio variance (risk) given constraints (e.g., long-only, fully invested).
   - هدف: stability / volatility reduction.

2. **Maximum Sharpe Ratio (Max Sharpe)**
   - Maximizes risk-adjusted return using the Sharpe Ratio (portfolio excess return over a risk-free rate divided by volatility).
   - هدف: best return per unit of total risk.

3. **Omega Optimization (Omega Ratio)**
   - Uses the Omega ratio to optimize allocations based on the full return distribution (not only mean and variance).
   - هدف: favor allocations with more probability-weighted upside relative to downside.

4. **Minimum Semi-Variance (Downside Risk)**
   - Minimizes downside variability (penalizing negative deviations more than positive ones).
   - هدف: reduce downside risk rather than total volatility.

## Backtesting & Benchmark Comparison

Each optimized portfolio is **backtested** over the historical period and compared against the **benchmark** to evaluate:
- performance behavior through time
- drawdowns / downside exposure
- relative risk-return profile vs the market proxy

## Risk & Liquidity Metrics

The analysis includes risk measures commonly used in portfolio risk management:

- **VaR (Value at Risk)**  
  Estimates the potential loss at a given confidence level over a specified horizon.

- **ES / CVaR (Expected Shortfall)**  
  Measures the average loss in the tail beyond VaR (more informative under fat tails).

- **Time to Liquidity / Liquidity Risk**
  Evaluates how quickly the portfolio could be rebalanced or liquidated given trading volume constraints, highlighting implementation feasibility and liquidity-adjusted risk.

## Final Proposed Strategy

Based on the comparative results, a final portfolio strategy was proposed:

### **CVaR-adjusted Semi-Variance Portfolio**
A strategy that combines:
- downside-risk control (semi-variance perspective)
- tail-risk awareness (CVaR/Expected Shortfall adjustment)

This final proposal aims to improve robustness in adverse market regimes while keeping the portfolio aligned with a moderate-risk mandate.

## How to Run

1. Open `PortfolioAnalysis.ipynb` in Jupyter Notebook / JupyterLab (or VS Code notebooks).
2. Install dependencies (typical stack used):
   - `numpy`, `pandas`
   - `matplotlib`, `seaborn`
   - `yfinance`
   - `scipy`
   - `scikit-learn`

Example (pip):
```bash
pip install numpy pandas matplotlib seaborn yfinance scipy scikit-learn
```

3. Run all cells to reproduce:
   - data download
   - optimizations (Min-Var, Max Sharpe, Omega, Min Semi-Variance)
   - backtests and benchmark comparisons
   - VaR / ES and liquidity analysis
   - final CVaR-adjusted semi-variance proposal

## Notes / Disclaimer
This repository is for educational and analytical purposes only and does not constitute financial advice. Market data quality and assumptions (risk-free rate, constraints, rebalancing rules, etc.) materially affect results.
